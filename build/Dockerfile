FROM quay.io/operator-framework/ansible-operator:v0.19.4

# Install kubectl.
COPY --from=wep4you/k8s-kubectl:1.19.2 /usr/local/bin/kubectl /usr/local/bin/kubectl

# Install Ansible requirements.
COPY requirements.yml ${HOME}/requirements.yml
RUN ansible-galaxy collection install -r ${HOME}/requirements.yml \
 && chmod -R ug+rwx ${HOME}/.ansible

COPY watches.yaml ${HOME}/watches.yaml

COPY main.yml ${HOME}/main.yml
COPY roles/ ${HOME}/roles/
