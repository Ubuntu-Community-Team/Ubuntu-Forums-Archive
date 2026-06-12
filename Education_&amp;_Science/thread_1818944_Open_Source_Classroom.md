---
title: "Open Source Classroom"
date: 2011-08-05
forum: Education &amp; Science
---

### Post by nseward on 2011-08-05
I am a computer science teacher at a magnet school and my window server just bit the dust hard. I thought this would be a wonderful opportunity to replace it with an open source server and also bring all 60 of our desktops over to the linux side of the street. The problem is that I need to pull this off seamlessly so my admin will see what a wonderful thing linux is. My goal is to get the whole school to transition but I have to do it myself first. 
 
Here is my wish list.
After desktop users login they have access to personal network storage and group network storage on the server. In their home drive is a personal web root directory. I want everything as automated as possible. I am going to have to deal with over 200 users. In fact, I am already planing on having an automated account creation webpage with email authentication. (This I will be able to figure out if I am pointed in the right direction for everything else.)
 
I am trying to increase my knowledge on ldap, samba, nss, kerberos, etc. The problem is information overload at the present moment. My server parts don't arrive until next week and I will only have a day or two to bring it all together. I would greatly appreciate any and all help/suggestions. I am not a linux dummy but I am overloaded on design choices at the moment and need proffessional help.

---

### Post by Basher101 on 2011-08-05
I can't help you with most of your wish list, but i know how you can save ALOT of time when you want to install it.

Step 1) Install Ubuntu or any desired distro you wish
Step 2) Install and configure it the way you would basically need it (install samba and other networking programs you would need for the server perhaps?)
Step 3) Install Remastersys and make a complete Backup of that Ubuntu where you installed the basic networking programs and made configurations.
Remastersys then creates a Live CD .iso image of that pre-configured system. This can then be burned to CD or DVD or copied to USB sticks using the Start up media tool inside Ubuntu
Step 4) Share and install it on the Desktops. It will run the usual installation progress, only that it also installs all the programs and configurations of the original it backed up. 

Hope this helps speeding up the installation :)

---

### Post by timlev on 2011-08-29
Hi,

More information on what the Windows server was used for would be more helpful:

Did it host the Student Informatin System? Printing? Teacher Websites? Email?

Was this just a domain server to organize the Windows computers?

From your wishlist, it sounds like it is mainly a domain server and network storage, though it also hints at teacher websites and email. If you want it all in one box, it sounds like there's a lot of breaking points and a lot of angry teachers knocking at the door (because they can't figure out the new computers/email system/classroom websites/etc.) Best of luck to you :)

PS. I am a teacher who has seen tears at the most basic technology training session, hence my fear at so many large changes all at once.

---

