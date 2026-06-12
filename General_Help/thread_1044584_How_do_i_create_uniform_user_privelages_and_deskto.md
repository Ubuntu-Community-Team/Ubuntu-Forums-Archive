---
title: "How do i create uniform user privelages and desktops"
date: 2009-01-19
forum: General Help
---

### Post by Saghaulor on 2009-01-19
I'm not sure how to ask part of my question, so I'll just fumble with it.

First, is there a way to set up a group with specific permissions, so that I don't have to manually set the permissions for every user, ie, I don't want any of my users to administer the system?

Second, is there a way to make the desktop appearance identical for all users? I want to restrict what they see so that they only have the network manager applet, firefox, and startup/shutdown button visible. I want this for all users.

---

### Post by dcstar on 2009-01-20
> **Saghaulor said:**
> I'm not sure how to ask part of my question, so I'll just fumble with it.

First, is there a way to set up a group with specific permissions, so that I don't have to manually set the permissions for every user, ie, I don't want any of my users to administer the system?

Second, is there a way to make the desktop appearance identical for all users? I want to restrict what they see so that they only have the network manager applet, firefox, and startup/shutdown button visible. I want this for all users.

[http://www.linuxhowtos.org/Tips%20and%20Tricks/using_skel.htm](http://www.linuxhowtos.org/Tips%20and%20Tricks/using_skel.htm)

---

### Post by Saghaulor on 2009-01-20
Thanks dcstar,

I've read that editing the /etc/skel directory can apply uniform profiles.

But I'm not sure what to do per se.

Should I do something like the following?
[LIST=1]
[*]Set up a profile the way I want it
[*]Copy the /home/username directory to /etc/skel
[*]use the useradd tool to create the user account
[/LIST]

I don't think that I need the entire contents of the /home/username directory, only specific configuration settings, like Mozilla, the appearance of Gnome, etc.

Am I on the correct track? More precise details would be most appreciated.

---

### Post by dcstar on 2009-01-20
> **Saghaulor said:**
> Thanks dcstar,

I've read that editing the /etc/skel directory can apply uniform profiles.

But I'm not sure what to do per se.

Should I do something like the following?
[LIST=1]
[*]Set up a profile the way I want it
[*]Copy the /home/username directory to /etc/skel
[*]use the useradd tool to create the user account
[/LIST]

I don't think that I need the entire contents of the /home/username directory, only specific configuration settings, like Mozilla, the appearance of Gnome, etc.

Am I on the correct track? More precise details would be most appreciated.

Anything that is in that directory is copied over to new user accounts when they are created.

Put things in there and experiment with creating new accounts (using the GUI method which uses useradd anyway AFAIK).

---

### Post by Saghaulor on 2009-01-23
For those who may ask the same question that I asked, here is my answer.

Though I'm not sure that I needed all of these folders, these are the folders that I copied to achieve a uniform desktop for all new user profiles.

Use the instructions as listed above, then copy the following folders to the /etc/skel folder, from your /home/username folder.

.config  .gconfd  .gnome2_private  .mozilla   .themes
.gconf   .gnome2  .local           .nautilus

I'm going to play around at some point to figure out exactly just what folders are required for uniform desktops.

---

