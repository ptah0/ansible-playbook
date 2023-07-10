# ansible-playbook

This ansible playbook is used to setup basic environment on new Debian/Ubuntu servers:

- vimrc
- oh-my-zsh

# How to use

Follow those steps:

1. Checkout code and setup python + virtualenv
   ```bash
   sudo apt install -y python3-virtualenv
   git clone https://github.com/ptah0/ansible-playbook.git
   cd ansible-playbook
   virtualenv --prompt ansible .venv
   source .venv/bin/activate
   pip install -U -r requirements.txt
   ```

2. Prepare `inventory` file
   ```bash
   cp inventories/example.yaml inventories/your_servers.yaml
   ```
   
   Modify the content of `inventories/your_servers.yaml` :

   - Replace *server.example.com* with your own server
   - Replace *example_user* with your own user
   
3. Verify `ssh` and `sudo` without password
   ```bash
   # using example.yaml
   ssh example_user@server.example.com
   sudo echo hello # make sure no password prompt
   ```
   
4. Run the playbook
   ```bash
   ansible-playbook -i inventories/example.yaml site.yaml
   ```
