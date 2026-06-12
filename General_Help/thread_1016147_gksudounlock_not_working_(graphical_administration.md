---
title: "gksudo/unlock not working? (graphical administration)"
date: 2008-12-19
forum: General Help
---

### Post by rhcm123 on 2008-12-19
I have ubuntu 8.04, recently vanilla installed. I was used to administering the computer by going to system, whatever I wanted, then hitting unlock in the corner, typing my password, and doing what i needed to do Thats what i did in 7.04.

But it dosent work now! Let's take networking. I usually just go System, administration, networking. I click unlock, then change whatever. Now i have to do it manually with /etc/network/interfaces (which isn't a problem, just a pain in the butt. Espescially printing....)

But now, the computer just sits there. I can't even force quit the window. Everything else locks up. About a minute later, I get a message "could not unlock: an unexpected error occoured".
I then tried gksudo network-admin. The window came up, but it was still locked! I also got the following output in the terminal:

```

ussr@USSR-LAPTOP:~$ gksudo network-admin

** (network-admin:7734): CRITICAL **: Unable to lookup session information for process '7734'
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
ussr@USSR-LAPTOP:~$ 

```

and if i try gksu:
```
ussr@USSR-LAPTOP:~$ gksu network-admin
(network-admin:7944): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (network-admin:7944): CRITICAL **: Unable to lookup session information for process '7944'
ussr@USSR-LAPTOP:~$ 

```

Does anybody know why gksudo isn't working?

---

### Post by taurus on 2008-12-19
Any problem using sudo from a terminal?

```
sudo apt-get update
```

---

### Post by rhcm123 on 2008-12-19
> **taurus said:**
> Any problem using sudo from a terminal?

```
sudo apt-get update
```

nope, sudo works fine. Never had a problem with it.
```
ussr@USSR-LAPTOP:~$ sudo echo blah blah blah
[sudo] password for ussr: 
blah blah blah

```

I actually just noticed this problem today. I've become used to using the command line, as my server is headless. So, instead of the graphical apps, i actually just configured my system entirely by hand. However, when I wanted to change some printing settings (which is a pain to do from the terminal), i found out that gksudo isn't working.

---

### Post by rhcm123 on 2008-12-23
i also just found out that synapic still works! I'm installing a plugin now... odd indeed.

---

