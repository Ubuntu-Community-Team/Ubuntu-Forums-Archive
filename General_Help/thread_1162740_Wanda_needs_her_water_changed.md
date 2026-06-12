---
title: "Wanda needs her water changed"
date: 2009-05-18
forum: General Help
---

### Post by mdgrech on 2009-05-18
The gnome applet called fish or more formerly known as Wanda the fish is misbehaving.  When you add the fish applet to your panel and click on Wanda to encouage her to swim across the screen you are instead greeted with the error:

**Unable to locate the command to execute**

Please help me save Wanda.

---

### Post by jms1989 on 2009-05-18
Double check Wanda's preferences for errors and check to see the the program to execute can be found from the terminal. Mine is set to "fortune", without quotes.

---

### Post by mdgrech on 2009-05-18
Solved:

sudo apt-get install fortune-mod

---

### Post by PinkRose on 2009-10-09
Thanks allot for you reply, It worked for me too

---

### Post by 3rdalbum on 2009-10-09
"Wanda needs her water changed"...

"Morning of April 1st"...

---

### Post by Kiting Illini on 2010-01-23
Thanks from me as well!

---

### Post by soluckytouselinux on 2010-02-18
> **mdgrech said:**
> Solved:

sudo apt-get install fortune-mod

Hi. Just to let you know that this really worked for me. Thanx

---

### Post by Soul_Architech on 2010-03-23
When I entered the sudo apt-get install fortune-mod I received 
E:Couldn't find package fortune-mod
I am still getting the same command error when I click wanda. Any suggestions?
thanks!

---

### Post by coffeecat on 2010-03-23
> **Soul_Architech said:**
> When I entered the sudo apt-get install fortune-mod I received 
E:Couldn't find package fortune-mod
I am still getting the same command error when I click wanda. Any suggestions?
thanks!

Have you refreshed the package metadata since you installed by:

Reload in Synaptic. Or..

Check in Update Manager. Or...

'sudo apt-get update' in the terminal?

Do a 'sudo apt-get update' first (make sure you have internet connectivity) and then try 'sudo apt-get install fortune-mod' once the update has finished.

By the way, I'm glad to see you're getting your priorities right with your first post. :p Welcome to the forum! :wink:

---

### Post by Soul_Architech on 2010-03-25
Thank you for your reply. Unfortunately no, I haven't been able to get my internet to work with Unbuntu yet. I have a wireless USB Linksys WUSB600 and am currently trying to figure out how to get that working. I thought I would play with Wanda to take a break, lol, instead I just found something else that I need to figure out how to fix. 
I uninstalled and reinstalled Unbuntu and did the "sudo-get install fortune-mod command" this time I recieved the message
sudo-get: command not found

---

### Post by coffeecat on 2010-03-26
> **Soul_Architech said:**
> sudo-get: command not found

That's because there is no "sudo-get" command. Re-read my and mdgrech's posts. And re-read my post about needing to refresh the metadata first before the system will "know" about the fortune-mod package - or virtually any other package for that matter. And for which you'll need an internet connection.

I had a glance at the other thread you've posted on. More than 34500 posts and growing! :-s Before you go any further, check this:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WUSB600N](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WUSB600N)

Version 1 of your card links to the thread you posted on. Version 2 is a different chipset and links to a bug report. If you haven't already, you need to identify which is your version. I can't help you any further with the wireless. You either need to get help on that megathread or start your own thread.

---

### Post by xsellout on 2011-03-25
I just changed the water with your help so thank you all!  I'm brand new here and on Linux and want to thank you for my very first Ubuntu fix.

Cheers

---

