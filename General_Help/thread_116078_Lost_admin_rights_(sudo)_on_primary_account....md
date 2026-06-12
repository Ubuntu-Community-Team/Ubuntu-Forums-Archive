---
title: "Lost admin rights (sudo) on primary account..."
date: 2006-01-11
forum: General Help
---

### Post by Onos on 2006-01-11
I am not entirely sure how this happened, but I seem to have lost my ability to do administrative tasks that would require the use of my **sudo** password:

**[COLOR="DarkRed"]- terminal:[/COLOR]** cannot use **sudo apt-get install <package_name>**

**[COLOR="DarkRed"]- System > Administration > Synaptic Package Manager:[/COLOR]** does not start up after asking my password


**[COLOR="DarkRed"]- System > Administration > Update Manager:[/COLOR]** Also fails to start after asking for password

**[COLOR="DarkRed"]- System > Administration > Users and Groups:[/COLOR]** Also fails to start after asking for password

**[COLOR="DarkRed"]- Firestarter:[/COLOR]** Fails to start up.


I think I might have borked it up when I added my wife as a sudo user temporarily, so she could load the uim and some Japanese language packages; I removed her sudo rights via the **[COLOR="DarkRed"]System > Administration > Users and Groups[/COLOR]** shortly after those packages were installed.

Does anyone have any ideas on how I might be able to fix this, or am I looking at another session of installing everything again? :confused:

---

### Post by 23meg on 2006-01-11
What error do you get when you use sudo in a terminal? Also, please post the contents of your /etc/hosts file.

---

### Post by hashimoto on 2006-01-12
Also check your sudoers file. If you have root account enabled, open terminal and do "su", then "visudo" and check that your username still is at the end of the file with correct rights. They should be the same as root has above that.

If you don't have the root account active, you need to boot into safe mode to gain root access and do this.

---

### Post by Onos on 2006-01-12
[QUOTE=23meg]What error do you get when you use sudo in a terminal? Also, please post the contents of your /etc/hosts file.[/QUOTE]

I will have to check out /etc/hosts when I get home... but as for sudo:

```
myadmin@computer:# sudo apt-get update
Password:
```

(I enter the password...)

```
myadmin@computer: #
```

There is no response for any activities done on the command line either (after exiting the GUI with the lovely CRTL-ALT-Backspace).

I will also check out visudo when I get back also.

---

### Post by Muskoka on 2006-01-12
Hi, I had the same problem a couple of days ago. I ended up going into "Run as different user" menu ( I think thats what its called, I'am not on my Ubuntu box right now, under "System tools" and type in users-admin. I think you will find if you look at your permissions that you will not have any. I had the same thing after I added a new user and I have no idea why it did it but it did....have a look. In otherwords every check box was unchecked.

Hope this helps....

---

### Post by Onos on 2006-01-12
I think I figured it out.... I had to use the root account to get to be able to use **visudo**.  It turns out that somehow, I managed to delete myself (primary account) from the "admin" group, which in Ubuntu seems to serve the same purpose as "wheel" (I think) in most other Linux distros.

Yay, I can now apt-get again to my heart's content! :D

---

### Post by kickenchicken on 2006-10-12
can anyone help me. same thing happened with my ubuntu. except when i try to enter the visudu %admin ALL=(ALL) ALL thing it says syntax error then something like "(" was unexpected. is there some other way? i have the live cd of ubuntu 6.06. i guess if i cant il re-install linx. i would have to reformat that partition right?

---

### Post by aysiu on 2006-10-12
Follow these directions:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

