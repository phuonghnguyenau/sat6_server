# satellite6-server
A nice little role to set up a Satellite 6 server from Red Hat CDN, including installing the application itself, importing subscrption manifest and setting up repositories.

## Requirements
* Internet access to Red Hat CDN. If using a proxy, this needs to be configured beforehand
* Satellite application should be set up in Red Hat Customer Portal already
* Server should be built already, either a VM, cloud instance or bare metal
* The server should be registered into Red Hat CDN already.
* File system creation/resize completed, if required

## Variables - To be overridden
### RHSM settings
* `rhsm_satellite_name` - the name of the Satellite referred to in RHSM
* `rhsm_username` - login username for RHSM (for accessing Red Hat CDN)
* `rhsm_password` - login password for RHSM (for accessing Red Hat CDN)

### Satellite Server config
* `satellite_admin_username` - Satellite admin user name that will be configured during deployment
* `satellite_admin_password` - Satellite admin password that will be configured during deployment
* `satellite_organization` - The default organisation for Satellite that will be configured during deployment
* `satellite_location` - The default location that will be configured during deployment
* `satellite_server_api` - The URL for the Satellite REST API
* `satellite_client_repositories_with_releases` - a YAML list of repositories to configure on Satellite
* `satellite_client_repositories_without_releases` - a YAML list of repositories to configure on Satellite, some repositories do not have any release info
* `satellite_gpg_keys` - A list of GPG keys to define in Satellite
* `satellite_custom_products` - Configure a custom product in Satellite
* `satellite_custom_repositories` - Configure a custom repository in Satellite
* `satellite_sync_plans` - Configure a custom sync plan for product(s)

## Other Variables
* `rhsm_repos_to_disable` - a list of repositories to disable (may conflict with Satellite install)
* `satellite_server_repos` - required repositories for Satellite install
* `satellite_package` - name of the Satellite package to install (currently 6.6)
* `rhsm_utils_repo_url` - Git repository for rhsmTools
* `rhsm_utils_repo_version` Git branch of rhsmTools `rhsm_utils_repo_url`
* `rhsm_utils_repo_dest` - directory to clone `rhsm_utils_repo_url` to

Tags
----
* `pre_install` - Preparing server for satellite install
* `install` - Actual install of satelite 6 itself
* `post_install` - Post install tasks to implement sane defaults
* `register_satellite` - Enabling communication for satellite to RHSM
* `setup_rh_products` - Enabling Red Hat products and repositories in Satellite for organization
* `setup_custom_products` - Enabling custom products and repositories in Satellite for organization, e.g. EPEL
* `setup_sync_plans` - Setting up a sync plan for products to ensure up to date repositories

License
-------

GPLv3

Author Information
------------------

Phuong Nguyen - Red Hat Consultant, RHCA