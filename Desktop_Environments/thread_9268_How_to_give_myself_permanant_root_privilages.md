---
title: "How to give myself permanant root privilages?"
date: 2004-12-26
forum: Desktop Environments
---

### Post by alphster on 2004-12-26
I want to have permanent root privelages (sorta like windows admin).

I don't want to logon as root either, I just don't ever want to type "sudo" ever again.  I want access to every folder and permission to delete what i want.

Is there a command to do this?

Thanks.

---

### Post by Shaggy on 2004-12-26
[QUOTE=alphster]I want to have permanent root privelages (sorta like windows admin).

I don't want to logon as root either, I just don't ever want to type "sudo" ever again.  I want access to every folder and permission to delete what i want.

Is there a command to do this?

Thanks.[/QUOTE]
 Well if you really want it you should just log in as root.  But you could just change the group that your user is in to the same one that the root user is under.

---

### Post by Rancoras on 2004-12-26
Very bad idea.  If a virus, trojan or whatever compromises your machine, then it has complete run of the machine if you are logged in.  This makes your machine no more secure than a windows machine at that point.  Typing sudo every once in a while is a small sacrifice for a more secure machine.

---

### Post by ahyden on 2004-12-26
If you open a terminal and type sudo -H -s you will have root privilages until you type exit. Saves some sudo typing if you're doing alot of admin stuff.

---

### Post by varunus on 2004-12-26
You want to have permanent root priviledges without being root?  Um...isn't this the same as being root?

To enable the root account in Ubuntu, just type "sudo passwd root" into a terminal...root will now be enabled.  You could change your user account to have root priviledges if you want by adding it to the root group...

Really, using sudo makes your system much safer though, but you could always log on as root if you wanted to.

---

### Post by feneks on 2004-12-27
Permanent root privelages for normal users is DANGEROUS!!!

But in the file /etc/group you will find a line
root: x: 0: root

convert it to 
root: x: 0: root,username

(I inserted some spaces to prevent smilies)

This should be enough to set all sysadmins cracy. :mrgreen:

I WOULDN'T  DO THAT !!!  8-[
You are warend!!

---

### Post by feneks on 2004-12-27
If this isn't enough to set hell on fire try this:

/etc/passwd  contains infos about the users.

set
[username] : x: [number(a)] : [number(a)] : [string you shouldn't touch]
to
[username] : x: [number(a)] : 0 : [string you shouldn't touch]


- Though my first posting should fullfill your perverted wishes.

---

### Post by AndersAA on 2004-12-28
putting yourself in the root group will not give you full root privileges... and you should never edit /etc/passwd directly.  There is a passwd tool for editing it.

what varunus will enable the root account

---

### Post by MacAdmin on 2004-12-28
Use sudo command when you needed.  It is dangerous to use root account for day-to day operation. :mrgreen:

---

### Post by mal on 2004-12-29
[QUOTE=alphster]I want to have permanent root privelages (sorta like windows admin).

I don't want to logon as root either, I just don't ever want to type "sudo" ever again.  I want access to every folder and permission to delete what i want.

Is there a command to do this?

Thanks.[/QUOTE]

What's wrong with Applications / System Tools / Root Terminal ?

Mal

---

### Post by Perfect Storm on 2004-12-29
[QUOTE=alphster]I want to have permanent root privelages (sorta like windows admin).

I don't want to logon as root either, I just don't ever want to type "sudo" ever again.  I want access to every folder and permission to delete what i want.

Is there a command to do this?

Thanks.[/QUOTE]

There is a reason why using sudo (or su on othe linux systems) when doing stuff, it's secure your system from be taken over by hackers and viruses (or making it more difficult). Try to get comfort with the commands and you'll discover it's much easier than point'n'click.


.:=The AI Dude=:.

---

### Post by Sol on 2005-11-22
Hi, as you're about to find out i'm about as newb as it comes... apart from using Linux to program at Uni. 
I need some help with the root system? I'm trying to install the graphics drivers for my Nvidia graphics card, and in order to install it i need to be root user, but i don't know what the password or user name is?

This is as far as i have been :
1) Log out and type "root" as the user name.
2)thought password was "root"... but it's not...

can anyone please help. 
thanks.
Sol

---

### Post by AndersAA on 2005-11-22
[QUOTE=Sol]Hi, as you're about to find out i'm about as newb as it comes... apart from using Linux to program at Uni. 
I need some help with the root system? I'm trying to install the graphics drivers for my Nvidia graphics card, and in order to install it i need to be root user, but i don't know what the password or user name is?

This is as far as i have been :
1) Log out and type "root" as the user name.
2)thought password was "root"... but it's not...

can anyone please help. 
thanks.
Sol[/QUOTE]

your not allowed to login as root on an ubuntu system, instead use sudo to give yourself temporary root access.
sudo <program to run (for example the nvidia install program)>

but instead of installing the drivers using nvidia's install program you can install them using synaptic, which is much simpler.  But you might have to add the universe repository.  Chances are threre's information on how  to do it in the wiki or on the forum.

---

### Post by aysiu on 2005-11-22
How do I make it so I permanently don't have to use a key to get into my apartment?

---

### Post by AndersAA on 2005-11-22
[QUOTE=aysiu]How do I make it so I permanently don't have to use a key to get into my apartment?[/QUOTE]

remove the door (on a side note, this thread is in warty 4.10 app support, it should go die :p )

---

### Post by dbott67 on 2005-11-22
[QUOTE=aysiu]How do I make it so I permanently don't have to use a key to get into my apartment?[/QUOTE]

Upgrade your door to Microsoft DoorXP.  Be sure to accept the default settings, as changing them could cause you to lock yourself out.

PS - don't forget to install Service Pack 2, as the first version put the keyhole inside the apartment, and the little doo-hickey that locks the door on the outside!  Talk about your buffer overflows!

---

### Post by Sol on 2005-11-22
Right sorted out the sudo/root jazz, but now need to install the Nvidia driver but it tells me that X needs to turned off...
I've consulted the read me for Linux drivers on the Nvidia website but it's not very clear.

Can someone please help me with how to change my run level? and install the graphics driver, then get my run level back to normal.

Oh and if you could explain to me if it's beneficial for me to change my run levels other then to disable X Windows...?

P.S thanks for helping me with my last query so quickly.
Sol.

---

### Post by AndersAA on 2005-11-22
make a new thread, this doesn't belong in the warty forum about root privilages ;)

---

