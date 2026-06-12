---
title: "Installing Deluge through synaptic?"
date: 2009-05-20
forum: General Help
---

### Post by fleaaccela on 2009-05-20
[http://packages.ubuntu.com/jaunty/all/deluge/download](http://packages.ubuntu.com/jaunty/all/deluge/download)

This page says this:
> If you are running Ubuntu, it is strongly suggested to use a package manager like [aptitude]("http://packages.ubuntu.com/jaunty/aptitude") or [synaptic]("http://packages.ubuntu.com/jaunty/synaptic") to download and install packages, instead of doing so manually via this website.I tried looking for it in synaptic through a search, but could not find anything. I tried installing this through the Package Installer:

[http://mirrors.kernel.org/ubuntu/pool/universe/d/deluge/deluge_1.1.6+dfsg-2ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/d/deluge/deluge_1.1.6+dfsg-2ubuntu1_all.deb)

But it comes up with an error message inside of the installer that says:

> Error: Dependency is not satisfiable: deluge-common (= 1.1.6+dfsg-2ubuntu1)I'm using Gnome 2.X. Not sure what I'm doing wrong here. Usually installing progs through synaptic is a breeze, but it's nowhere to be seen - even though the site states that it is available for download through it.

Help? (ps - been using Ubuntu for about 5 days, pretty much straight "out of the box". This is my first problem.)

---

### Post by mb_webguy on 2009-05-20
Adding [this PPA]("https://launchpad.net/~deluge-team/+archive/ppa") to your software sources should fix any problems with installation, and also make sure you have the most up-to-date version of the application.

To add the PPA, open System > Adminitration > Software Sources, go to the Third-Party Software tab.  Click on the Add button, and paste the appropriate line for your version of Ubuntu from the PPA page.  For example, if you're using 9.04 (Jaunty Jackelope), you'd paste the following line in the textbox.```
deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main
```Now click the Close button.  Don't bother reloading your sources when prompted (since we're about to do it a different way anyway).

Now we need to add the PPA key.  We *could* do this using the GUI, it's unfortunately not as straightforward as it should be.  (There are people working on better integration with Launchpad and making the addition of PPAs easier, but we're not there yet.)  Open the terminal (Applications > Accessories > Terminal) and enter the command "sudo apt-get update".  You'll get an error message about a missing GPG key, which will include a long string of letters and numbers.  Enter the following commands, replacing *key_id* with that alphanumeric string.```
gpg --keyserver keyserver.ubuntu.com --recv *key_id*
gpg --export --armor *key_id* | sudo apt-key add -
```Now enter the command "sudo apt-get update" again.  You should no longer get the error.  Now you should be able to install Deluge with no problems.

---

