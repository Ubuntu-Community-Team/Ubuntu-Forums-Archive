---
title: "make a panel launcher run as different user?"
date: 2005-02-26
forum: Desktop Environments
---

### Post by linuxgrrl on 2005-02-26
hi,
I would like to be able to start mythtv with a gnome panel launcher.

But, mythtv must be run as a different user, "mythtv." 

I found the "run as different user" option on the menu, which works fine but it needs a keyboard, so doesn't work too well from the living room couch :)

How do I create a custom panel launcher that will run "mythfrontend" as user "mythtv"? I assume if I give that user no password, I can then launch with one click.

Thanks,
Mary

---

### Post by apoc on 2005-02-28
Hey, how about adding yourself to that group ?

---

### Post by bored2k on 2005-02-28
[QUOTE=apoc]Hey, how about adding yourself to that group ?[/QUOTE]

or just in terminal type
sudo username mythtv
and enter the other user's passwd .

---

### Post by linuxgrrl on 2005-03-03
[QUOTE=apoc]Hey, how about adding yourself to that group ?[/QUOTE]

alas, this did not work.

and using "sudo" from a terminal, while effective, does not work from the couch w/o a keyboard.

is there a way to add a launcher to the panel that will start it as a different user?  my non-techie gf wants to use mythtv but she won't do anything involving "sudo".
thanks.

---

### Post by bored2k on 2005-03-03
[QUOTE=linuxgrrl]alas, this did not work.

and using "sudo" from a terminal, while effective, does not work from the couch w/o a keyboard.

is there a way to add a launcher to the panel that will start it as a different user?  my non-techie gf wants to use mythtv but she won't do anything involving "sudo".
thanks.[/QUOTE]

this is fairly easy
apt-get install xnest

this is allow u to open another user window INSIde another user
after installed go to applications > sys tools >  nested login [or whatever]


then u configure GDM to autologin to ur GF's after ... 15seconds , that way theres no typing involved ... et voila ... a user INSIDE a user

---

### Post by bigzak on 2005-03-04
[QUOTE=bored2k]this is fairly easy
apt-get install xnest

this is allow u to open another user window INSIde another user
after installed go to applications > sys tools >  nested login [or whatever]


then u configure GDM to autologin to ur GF's after ... 15seconds , that way theres no typing involved ... et voila ... a user INSIDE a user[/QUOTE]
 Do this:

chown mythtv /path/to/mythtv
chmod +s /path/to/mythtv

The +s makes the program 'suid' (set user ID) and it will run as the mythtv user. This is similar to making cdrecord run with root privileges. See `man chmod` for more information.

---

### Post by holomorph on 2005-05-28
[QUOTE=linuxgrrl]hi,
I would like to be able to start mythtv with a gnome panel launcher.

But, mythtv must be run as a different user, "mythtv." 

I found the "run as different user" option on the menu, which works fine but it needs a keyboard, so doesn't work too well from the living room couch :)

How do I create a custom panel launcher that will run "mythfrontend" as user "mythtv"? I assume if I give that user no password, I can then launch with one click.

Thanks,
Mary[/QUOTE]
 In case you didn't find a solution, or like me wanted to be able to lanch an app (in my case thunderbird) as more than one different user with a single click, here's the trick:

I create a launcher of the program I want to run as another user on my panel, then right click and go to properties.  Then under command put "gksu -u <username> " in front of the command.  So, to run thunderbird as the user "bob", the command is `gksu -u bob mozilla-thunderbird`.

Hope that is helpful to someone, I know I've been looking for a good solution to that for a while :P

---

