---
title: "gimp problem"
date: 2012-02-25
forum: Desktop Environments
---

### Post by apoorv.jain on 2012-02-25
hi...
m on ubuntu 11.10.
i want to install gimp on my desktop.
i used Ubuntu Software Centre.
But this messsage occurs:

''This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.''



The following packages have unmet dependencies:

gimp-console: Depends: gimp (= 2.7.5-2012020901~oo) but 2.7.5-2012020901~oo is to be installed
              Depends: libfontconfig1 (>= 2.8.0) but 2.8.0-3ubuntu2 is to be installed
              Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.24.0-1ubuntu1 is to be installed
              Depends: libglib2.0-0 (>= 2.31.2) but 2.30.0-0ubuntu4 is to be installed
gimp-gap: Depends: libc6 (>= 2.7) but 2.13-20ubuntu5 is to be installed
          Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.24.0-1ubuntu1 is to be installed
          Depends: libglib2.0-0 (>= 2.24.0) but 2.30.0-0ubuntu4 is to be installed
          Depends: libgtk2.0-0 (>= 2.9.0) but 2.24.6-0ubuntu5 is to be installed
          Depends: libjpeg62 (>= 6b1) but 6b1-1ubuntu2 is to be installed
gimp-gmic: Depends: libc6 (>= 2.4) but 2.13-20ubuntu5 is to be installed
           Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed
           Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.24.0-1ubuntu1 is to be installed
           Depends: libgimp2.0 (>= 2.4.0) but 2.7.5-2012020901~oo is to be installed
           Depends: libglib2.0-0 (>= 2.24.0) but 2.30.0-0ubuntu4 is to be installed
           Depends: libgtk2.0-0 (>= 2.18.0) but 2.24.6-0ubuntu5 is to be installed
           Depends: libstdc++6 (>= 4.1.1) but 4.6.1-9ubuntu3 is to be installed
           Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed
           Depends: gimp (>= 2.6) but 2.7.5-2012020901~oo is to be installed
gimp-gutenprint: gimp-plugin-registry: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed
                      Depends: libjpeg62 (>= 6b1) but 6b1-1ubuntu2 is to be installed
                      Depends: libstdc++6 (>= 4.6) but 4.6.1-9ubuntu3 is to be installed




plz help me.....

---

### Post by Rodney9 on 2012-02-25
Try ```
sudo apt-get update && sudo apt-get upgrade
``` in the terminal.

Then try installing Gimp again.

Rodney

---

### Post by apoorv.jain on 2012-02-25
thanks for your reply....:)

i've tried but same thing is happening..

---

### Post by sudodus on 2012-02-25
It should work with the Software Center but try this terminal command
```
sudo apt-get install gimp
``` It should try to install a version of gimp that is compatible with your system. Maybe you need to purge it first:
```
sudo apt-get purge gimp
```
```
sudo apt-get install gimp
```
*Edit: Did you get any error messages when running the update and upgrade commands suggested by **Rodney9***

---

### Post by klaudiaru on 2012-02-25
Hi!, 

Try this:
[http://altinukshini.wordpress.com/2012/02/16/gimp-depends-libglib2-0-0-2-31-2-but-2-30-0-0ubuntu4-is-to-be-installed/](http://altinukshini.wordpress.com/2012/02/16/gimp-depends-libglib2-0-0-2-31-2-but-2-30-0-0ubuntu4-is-to-be-installed/)

and good luck

---

### Post by kayosiii on 2012-02-27
[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn)
read the instructions on this page - you need to add two more repositories

---

