---
title: "possible problem with forum search and ? about programs not starting from menu"
date: 2006-02-23
forum: Desktop Environments
---

### Post by crowdofone on 2006-02-23
Hello all. :) 

While using the forum i noticed that typing: 'program not loading' will result in the search term: 'program -loading'. as it is often things *not* working that people are searching for answers to the use of this expression seems problematic .. i also tried ' "program not loading" ' with identical results. 

secondly i seem to be having a problem on a new install of breezy. when i click on an application from the menu that requires superuser access (say network-admin) the superuser password box comes up and i enter a password but nothing loads. i have already added myself as a user to the sudoers file (before i wasn't even getting the password box). 

btw after install i was receiving the getbyhostname error and although that seems to have disappeared since using network-admin to setup my nic i have noticed that when doing a ifconfig i have only 'eth0' listed and no 'lo' .. is this weird?

ps. many thanks to ubuntu and the people that support it

---

### Post by joshuapurcell on 2006-02-23
Wierd problems for a new install. Try opening up a command prompt and running a command that usually would require you to sudo (for instance **sudo ethtool eth0**). Does it give any errors before or after you get prompted for the root password? You shouldn't have to enter your own username in the sudoers file... it should be done automatically at install.

EDIT: What are the exact error messages you are getting related to the 'getbyhostname' error? Did you have to enter the hostname of your system using the network-admin tool, or was there already a name for your machine listed?

---

### Post by crowdofone on 2006-02-24
did 'ethtool eth0' as sudo and nothing happened .. then tried as root and got the response: 'settings for eth0' ... then realised that i must have set up sudoers wrong .. so thats sorted and programs run from the menu now :p 

(i think my problem was in thinking that it was working because the password box was appearing .. as opposed to the silent treatment i was getting before editing sudoers)

funny that you mention it should of been handled automatically during install as this is precisely the same problem i had with breezy preview on a different machine .. it was well documented and i imagined it was just a bug in the preview but now i think about it on both installs i selected expert installation (due to only needing the base system and not the gigabyte's of the standard ubuntu install.) So maybe its a bug/feature of doing an expert install.

oh and lastly i just did a ifconfig after sorting sudoers out and 'lo' has mysteriously appeared :p 

many thanks for you your fast as lightning response and help in sorting this out joshua

---

### Post by joshuapurcell on 2006-02-24
The thing about choosing the expert install is that it leaves it up to the user to select certain install configurations manually (which isn't the case with the normal install route). I ran into problems the first time I did an install using the expert route as well, but once I figured out what options to select (and the order in which to select them) then my installs turned out how I intended them to be.

---

