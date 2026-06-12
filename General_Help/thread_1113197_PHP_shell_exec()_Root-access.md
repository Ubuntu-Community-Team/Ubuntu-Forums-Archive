---
title: "PHP shell_exec() Root-access?"
date: 2009-04-01
forum: General Help
---

### Post by mha2908 on 2009-04-01
I've got an Apache2-server with PHP5 installed on Ubuntu Server 8.10. I've tried to run the exec(), shell_exec() and system()-commands with the 'killall java' as the command. Nothing happens. If i type 'whoami' instead it writes out "www-data". How can I give PHP root-access?

Plz tell me in a very understandable language or with an easy guide, as I am NOT very good at Linux.

---

### Post by mha2908 on 2009-04-01
plz help me with this one...i'm falling apart here!

---

### Post by mb_webguy on 2009-04-02
Giving PHP root access is a Very Bad Thing.

Consider this example.  You have a text box that allows the user to enter information, which is then displayed on the page (such as for validation, or as a message board post).  If the text box data isn't properly validated, the user could type something like "><?php exec('shutdown now'); ?>", which would be executed by PHP rather than displayed.  If PHP is run as root, you can see how this would be a *major* security vulnerability, allowing anyone to run arbitrary commands on the system as root.

---

