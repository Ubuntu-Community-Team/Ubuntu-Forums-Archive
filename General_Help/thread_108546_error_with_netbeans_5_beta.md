---
title: "error with netbeans 5 beta"
date: 2005-12-26
forum: General Help
---

### Post by k_smolka on 2005-12-26
hi guys

i am having problems while installing netbeans 5

i have followed the instructions on the site but get the following error, 

does anyone have any ideas what this means

The wizard cannot continue because of the following error: could not load wizard specified in /wizard.inf (104)
WARNING: could not delete temporary file /tmp/ismp001/6553932
WARNING: could not delete temporary file /tmp/ismp001/9295395

many thanks

karl

---

### Post by arjun on 2006-01-05
Hey, I had the same problem and just fixed it.  What you have to do is update your JAVA_HOME and PATH variables.  ALot of people will tell you to do this in the /etc/profile file; but, this does not work or some reason.  Instead, edit /etc/bash.bashrc and at the bottom add the following lines:

JAVA_HOME=/opt/jdk1.5.0_06 
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH

NB.  You must put the location of YOUR jdk in the JAVA_HOME variable.  The location of mine was given for reference.

Now go ahead and install netbeans.

---

