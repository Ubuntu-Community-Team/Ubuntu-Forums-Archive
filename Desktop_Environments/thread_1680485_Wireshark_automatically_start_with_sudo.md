---
title: "Wireshark automatically start with sudo"
date: 2011-02-02
forum: Desktop Environments
---

### Post by DanHorniblow on 2011-02-02
Hi, I am trying to use wireshark on my ubuntu 10.10 laptop.

However I have found out that wireshark will only detect my network cards when it is started with root permissions.

How would I make it automatically start with root permissions?

---

### Post by Lampi on 2011-02-02
you can get rid of the password prompt, if you add a NOPASSWD ruleset for wireshark to your /etc/suoders file:

Here's a first guide how you set it up:

[http://help.ubuntu.com/community/Sudoers](http://help.ubuntu.com/community/Sudoers)

Be careful, always use the visudo command to edit the file (instead of gedit or kwrite) - visudo will parse the content before /etc/sudoers is stored. So you can't safe a file with invalid content sudo won't understand.

Nevertheless it's quite easy to mess up a system, if the file is not properly set up.

Here's the basic idea of the rule you would like, put it at the bottom of /etc/suoders using the visudo command:

```

DanHorniblow ALL=(ALL) NOPASSWD:/usr/bin/wireshark
```

Meaning:
The User DanHorniblow
on *any* host as *any* user [that's what ALL=(ALL) is]
can run without a password /usr/bin/wireshark

Make sure the rights of /usr/bin/wireshark are set to 0755, so no one but root can replace it to gain root access to your system.

You can set up more complex rulesets but that's up to you to find out

No you should be able to start wireshark with sudo /usr/bin/wireshark, without the password prompt

---

### Post by wojox on 2011-02-02
Go into Main Menu aka Alacarte and find wireshark and add "gksudo" to the beginning of it. 

Or just start it from your terminal with "gksudo wireshark"

---

