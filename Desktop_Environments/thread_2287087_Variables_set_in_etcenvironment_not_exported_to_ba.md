---
title: "Variables set in /etc/environment not exported to bash form Terminal"
date: 2015-07-16
forum: Desktop Environments
---

### Post by dan184 on 2015-07-16
Running Xubuntu 14.04.2 LTS

Hi Everyone!  I setup my proxy servers in /etc/environment and the proxies are picked up correctly in Firefox and Chromium, however when I open a bash shell using Terminal or xterm, the variables are not exported into the new shell.  I can verify this by using "echo $http_proxy" and listing the environment variables using the export command.  However, if I ssh into the system, the variables are correctly export into the bash shell.  Any ideas what might be going on here?  This is a default installation and I have not modify .bashrc, or .profile in the user or etc directories.  Thanks in advance!

---

