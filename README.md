# Blacklight Ansible Container

*NOTE:* This is used to provision a CENTOS 7 container for use with Blacklight application development

## Instuctions

(Substitute BLACKLIGHT_APP with the name of the Blacklight app you wish to use. The app username is the name of your Blacklight app.)

If you are working from an existing Git repository, first clone the project: `git clone PROJECT_GIT_URL BLACKLIGHT_APP`, otherwise create the project
directory: `mkdir BLACKLIGHT_APP`.

To provision the server:

- Change your directory to the project directory `cd /PATH/TO/BLACKLIGHT_APP`
- Install [ansible-container](https://www.ansible.com/ansible-container).
- Clone the blackligh-ansible-container ansible files `git clone https://github.com/skng5/blacklight-ansible-container.git BLACKLIGHT_APP`
- `cd BLACKLIGHT_APP`
- Change the name of your application in `ansible/container.yml`, `main.yml`, and `playbook.yml`.
- Build the container: `ansible-container build`
- Run the container: `ansible-container run`
- In a separate terminal, log onto the container `docker exec -it ansible_BLACKLIGHT_APP_1 su - BLACKLIGHT_APP`

To create a new Blacklight application:

- Go to the application directory: `cd /var/www/BLACKLIGHT_APP`.
- Create a rails app: `rails new .`
- Add the Blacklight and and any other gems you need to the Gemfile.
- Build the application: `bundle install`.
- Migrate the database: `rake db:migrate`

If this is from a cloned repository:

- Install the required gems: `bundle install`

For both new and cloned projects:

- In one terminal or session, start Solr: `solr_wrapper`
- In another terminal or session, start the blacklight application: `rails server -b 0.0.0.0`

Solr should be accessible at http://localhost:8983
The application should be accessible at http://localhost:3000
