---
title: "Why does Gnome2 work under sudo but not by any other way?"
date: 2009-03-22
forum: General Help
---

### Post by Shawn K on 2009-03-22
I'm trying to learn the "Inside Baseball" aspects of why Linux works the way it does, and I have a question.

I use Gnomad2, which is a program for downloading MP3 files to older Creative MP3 players.  If I go to *Applications > Sound & Video > Gnomad 2* and try to use the program, it says that it sees no device connected to USB.  However, if I open terminal and run it under *sudo gnomad2*, it sees the device normally and everything works fine.  As best as I can tell, the only thing I gain with sudo is making it see the USB connection.

Why would a program not work through normal links, but work properly under sudo?  What's going on at the program level that would cause that?  Is there anything I can do to change it?

---

### Post by James_Lochhead on 2009-03-22
The sudo command lets you execute a command as the root user. The root user is the super user - the user that can be do anything and everything to your system. 

Normally everything inside the filesystem except /home/<username> is owned by root. This is a security aspect that makes Linux very secure.

You are executing your program graphically as a normal user. Obviously that user does not have the correct permissions to view the device connected via USB. There are two solutions:

Edit the menu item so that gksudo is added in front of the original command.

OR

Leave the menu item alone and try and resolve the ownership issues with the USB device. I am not quite sure how to do this but I am sure someone will come along who does.

By the way:

How are you mounting the USB device?
and
Do you have multiple users on the system?

---

### Post by Shawn K on 2009-03-22
I'm the only user on the system.

As for mounting the USB drive, I'm afraid that I'll need you to explain to me exactly what that is.  All I know is, active USB ports just kind of "appeared" after I installed Ubuntu on my system.  I've taken it for granted.  Perhaps it's time I learn more about that, too.

Part of why I installed Ubuntu was to give myself a crash course in How Computers Work. ;)

---

