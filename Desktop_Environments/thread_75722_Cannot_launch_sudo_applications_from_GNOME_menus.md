---
title: "Cannot launch sudo applications from GNOME menus"
date: 2005-10-14
forum: Desktop Environments
---

### Post by dchart on 2005-10-14
I appear to be unable to launch any application that needs to be sudo'd from the GNOME menus. Synaptic does nothing; other applications think for a bit, but don't actually launch.

I can launch them from the command line with sudo, and use them, so they are installed and functional. gksudo is installed.

This isn't a fatal problem because there's a workaround, but it's annoying. Any ideas?

---

### Post by kwisatz on 2005-10-14
I had the same problem...I have edited /etc/sudoers and added my username...

---

### Post by g14 on 2005-10-14
[QUOTE=kwisatz]I had the same problem...I have edited /etc/sudoers and added my username...[/QUOTE]

Adding your username into the sudoers file is the WRONG way to do this. There is an admin group created for sudo access. If you really have to hand edit a file, add your name to the admin group in /etc/group.

Log in as the user you created during the installation. By default, this user is in the admin group. Go to System --> Administration --> User something (I am doing this from memory). Find your user and go to properties. Under one of the tabs it shows the ability to "Perform Administrative tasks" Check that box and it will ad you to the admin group and then sudo will work :)

---

### Post by dchart on 2005-10-14
Thanks for the replies, but they don't address my problem. My username is already in sudoers and I'm already in the admin group.

sudo works. It just doesn't work from the GNOME menus. GNOME is being run as me, so it should be fine.

---

### Post by Stormy Eyes on 2005-10-14
dchart, are you setting the menu items to use "sudo $command" or "gksudo $command"? Having gksudo isn't much use if you're not using it.

---

### Post by dchart on 2005-10-14
I've not set anything, so I'm using the default. When I turn one of the menu items into a button, so that I can look at the properties, it's using gksudo.

(I assume there's a way to look at the menu properties directly, but I don't know what it is.)

Thanks for your help.

---

### Post by dchart on 2005-10-14
Following up to myself -- I've just tried launching gksudo from a terminal again. I thought I'd done that before, but maybe not, as it died with a segmentation fault.

I find it hard to believe that gksudo is completely broken on all PowerPC machines, as someone would surely have noticed. Any suggestions as to what might be wrong with my installation?

(Upgrade from hoary was not smooth, but apt-get eventually seemed happy that everything was installed and working right.)

---

### Post by hanzj on 2005-10-15
I'm having the same problem, too, on my x86 machine. I think all the applications that need sudo access are not working.

I checked synaptic's icon and the command for that is "gksudo /usr/sbin/synaptic"

I ran that command in terminal: 
```
gksudo /usr/sbin/synaptic
```

and I got:
> Launching a SCIM daemon with Socket FrontEnd...
Segmentation fault
Synaptic didn't load.

Then I tried
```
sudo /usr/sbin/synaptic

```
giving me this output:> 
Launching a SCIM daemon with Socket FrontEnd...

(synaptic:8292): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:8292): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed



Then, synaptic launched.

What's wrong? In my hoary hedgehog days, I didn't have this problem. In my hoary days, when i clicked on synaptic from the menu, i'd get a dialog screen asking for the password. But in breezy, these icons/shortcuts don't work at all.

---

### Post by dchart on 2005-10-16
gksudo segfaults if it's in the Japan timezone? I'm in Japan as well, which is the only obvious common feature. There's no way it segfaults in every installation; Canonical's QA is better than *that.*

---

### Post by hanzj on 2005-10-16
I don't know whether Japan has anything to do with problem. I am currently in Japan, but I run Ubuntu in ENglish.

---

### Post by dchart on 2005-10-16
So do I, but I have the timezone set to Japan.

It's something we have in common, so maybe it's the problem...

---

### Post by iamhimay on 2005-10-16
Hi all,
I think I solved this problem. I had the exact same issue after my breezy upgrade. I uninstalled everything scim related, in synaptic, with a complete removal. Then I gradually installed the components I needed (Japanese, non-cjk package for Russian, etc.). Then I re-installed the gtk frontend for scim, which I thought was the problem.  I thought it was necessary for phonetic cyrillic input, but it's not. I think the problem is in the scim-m17n package, since when I reinstalled that I had the same problem again. All seems ok so far. I can open the programs in the System Admin menu with the pop up password dialog. Scim defaults to yawerty, which I'm not used to, but in gtk2 apps the transliterated Russian setting still works. All's well that ends well. 
Himay

---

### Post by dchart on 2005-10-17
Thanks for the suggestion. I don't have exactly the same problem (scim-m17n is not installed), but I'll try the analogous procedure and see what happens.

---

### Post by dchart on 2005-10-17
Right, the incompatibility appears to be with scim-gtk2-immodule on my system. I wonder why it's fine on yours? Unfortunately, I need that. Time to report a bug.

Thanks for your help.

---

### Post by daahli on 2005-10-28
hey guys,

I now have the exact same problem, however I do not have any of the scim modules installed. Any clue what else it might be?

---

### Post by x86i on 2005-11-10
I am having this same issue, on a brandnew install of 5.10. I do not live in Japan, and have not installed any new software. I discovered this problem upon logging in for the first time. Any ideas?

---

### Post by x86i on 2005-11-10
I've been informed that this is actually a problem with the updated packages. Unless somenoe can shed some more light on it, otherwise, Im lost.

The odd this is, this only happens on my laptop. Which is an older model gateway. Pentium 3 etc.


So if anyone has some work arounds, please let me know. Or anyone know, since this doesn't seem like something small.

---

### Post by hanspb on 2005-11-23
I have the same problem, gksudo segfaulting. With me, also Firefox is segfaulting. Both happened the first time after I had played around with the properties for the Gnome Panels, setting them to a transparent background. Firefox is ok on my other user. That one is not in the admin-group, so I can't test gksudo there. Does noone have a good solution to this?:(
I have nothing SCIM-related installed, as others have had problems with.

---

### Post by uhu_maotouying on 2005-12-09
Hi friends,

i updated from Hoary 5.04 to Breezy 5.10.  After restarting the system, i have found that i could not start (m)any of the sudo'ed programs from GNOME. I have also noticed the very same GTK & Chinese SCIM related error messages, when i started the application using the terminal, the applications, however, started flawlessly though.

However, i followed your hints and i found in my user-profile, that my "name" was associated with the group "name". After I have changed the group to "admin" everything went fine ... until now.

Hmmm

---

### Post by Daniel Ibrahim on 2005-12-09
Hello all, I have the problem that I can launch a field that asks me a password, however, when I enter the password, the field closes and nothing else happens...

 I thought that this was a problem of installation, because I didn't install the admin user (I had to do advanced installation because I wanted to keep some data on some of my hard drive (I have kept /home on a different partition)

Now I don't know exactly what to do, I have launched all the problems as root, but I cannot launch them from the Desktop.

I have already changed my default user and given access to most functions (by way of typing users-admin as root)
I have checked all the boxes in my primary user properties field...

what else do I have to do to use the menu?

---

### Post by twyt88 on 2005-12-09
Dear all,

For those who are still having problems with scim and gksudo, here's my 2 cents

I had this installed in my system to get Chinese input going:

ii  scim                   1.0.2-3         Smart Common Input Method platform
ii  scim-chewing           0.2.0-2.1build1 Chewing IM engine module for SCIM
ii  scim-chinese           0.4.2-2build1   Smart pinyin IM engine module for SCIM
ii  scim-config-gconf      1.0.2-3         GConf configure module for SCIM
ii  scim-config-socket     1.0.2-3         Socket configure module for SCIM
ii  scim-frontend-socket   1.0.2-3         Socket front end module for SCIM
ii  scim-gtk2-immodule     1.0.2-3         GTK2 IMModule with SCIM as backend
ii  scim-hangul            0.1.2-1build1   Hangul Input Method Engine for SCIM
ii  scim-server-socket     1.0.2-3         Socket IM engine module for SCIM
ii  scim-tables-ja         0.4.3-2         SCIM Japanese Input Method table data (Hirag
ii  scim-tables-ko         0.4.3-2         SCIM Korean Input Method table data (Hangul,
ii  scim-tables-zh         0.4.3-2         SCIM Chinese Input Method table data (WuBi,
ii  scim-uim               0.1.3-2build1   UIM IM engine module for SCIM

And like you it is segfaulting with gksudo. So starting at the bottom of the list I uninstalled scim-uim and it works.

So try that ...

twyt88

---

### Post by Daniel Ibrahim on 2005-12-10
[QUOTE=twyt88]
For those who are still having problems with scim and gksudo, here's my 2 cents
[/QUOTE]

I have scim not installed (I never had), it still does have problems. I will try what happens with scim.

what else is changing if you remove scim-uim?
I will try and install it and then uninstall again...

installed scim-uim (and all other dependencies)

menu for synaptic and all other sudo things doesn't work
removed scim-uim (only this) and still no change.

I suggest that now we can be sure that this doesn't have anything to do with scim packages.
at least there must have happened something else, when you uninstalled the scim-uim ...

---

### Post by espial on 2006-07-06
Hey Hey,

I've just encountered what seems to be this problem from a clean install of Ubuntu 6.06 (my first ever ubuntu install)

So whilst I can probably fix it using the advice here, my quesiton is this:

[INDENT]Why does this happen out of the box?

is it designed like this, or is it a flaw?

if it's a flaw why hasnt it been fixed?[/INDENT]


So whilst I'm fairly techie and competant I dont want to spend hours mucking around trying to get basic things to work.

---

### Post by dchart on 2006-07-06
It works for me with a clean install of 6.06, even with scim installed. I thought they'd fixed the problem.

---

