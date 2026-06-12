---
title: "Ubuntu Breezy + Network Security"
date: 2005-10-15
forum: Desktop Environments
---

### Post by goofeedude on 2005-10-15
Hello everyone,
 This is my first post on UbuntuForums, and I have a couple of things to say and ask. 
 First of all, Ubuntu is *slick*! I have been using linux off and on for about 3 years, and have tried about 28 different distributions, and Ubuntu knocks all their socks off when it comes to UI and usability, and the user community rocks, there are so many knowledgeable people ready to help. Truly amazing.

 Now to my questions. Right now I am dual-booting Slackware 10.2 and WinXP Pro. I am moving from my house to a residence hall on campus (been a student there for a year and half, but just now moving haha). My concern is security. I have pretty much decided, that if I could not boot Windows into this unknown environment, that would be awesome. (I don't trust Windows on an unknown network any farther than I could throw Bill Gates.) So off to Linux full time!

 My main questions are
1) How would you go about keeping Ubuntu secure in an unknown environment? What services are running by default upon fresh install?

2) In my current install of Breezy, eth0 is not active by default, and on every boot, I have to enable it through the network settings dialog in the System menu. How can I make this automatic?

Thanks for reading. Any replies would are greatly appreciated! :-)

---

### Post by khc on 2005-10-15
By default, no network services accept outside connections.
You should be able to do that in the same network setting dialog. Or you can put this in your /etc/network/interfaces:

auto eth0

I usually put it right before "iface eth0 ...", but I don't think it's required.

---

### Post by SickTwist on 2005-10-15
As khc said, Ubuntu is very secure out of the box. If you use strong passwords and the computer is physically secure then you have little to worry about.

If you plan to run ssh or some other type of server that is a different story and those services should be examined more closely. Additionally, there is no firewall set up after a default Ubuntu install. Since there are no outside services running this isn't much of a concern. However, one should probably set up a firewall if turning on remote services.

---

