---
title: "[SOLVED]There was an error starting the GNOME Settings Daemon... Ubuntu 8.10"
date: 2009-02-25
forum: Desktop Environments
---

### Post by knlgSeekr on 2009-02-25
So on day 4 of my Ubuntu 8.10 installation, i decided it was time to customize my desktop and install some cool themes and customize my desktop..

I did so, had lots of fun modifying metacity.xml files & finally got my desktop looking just how I wanted it. So as with every modification, it was time for the final test, rebooting the machine.

I closed out the programs i had open & ran sudo reboot
-upon rebooting, i noticed my desktop was taking longer than usual to load up and once it did, my customized font colors appeared for a second or two and then reverted to the regular theme that was there before maybe an hour of customization and tweaking.. lol

I clicked on system / preferences / appearance, and immediately got the error "There was an error starting the GNOME Settings Daemon. Some things, such as themes, sounds, or background settings may not work correctly.. "

-now i'm kicking myself for not recording the exact error because the next part of that message was unlike anything else i've been able to find while i was searching for a fix to the problem.. the next part said something like "this might be caused by another theme service such as KDE trying to start.."

anyway, after searching for a while & not being able to find any info that seemed to relate to my issue (system clock was fine, nothing about a remote application not sending a reply..) i decided to removing KDE and the files related to it from my system.

but first, i uninstalled emerald:

[COLOR="Navy"]sudo apt-get remove emerald
sudo apt-get autoremove emerald
sudo reboot[/COLOR]

this didn't resolve the issue, same lag loading the desktop, and same error when i went into system / preferences / appearance

so i decided to get rid of KDE, i ran:

[COLOR="Navy"]sudo apt-get remove KDE
sudo apt-get autoremove KDE[/COLOR]

then i removed all the KDE entries from synaptic (system / administration / synaptic packet manager)
[COLOR="Navy"]
sudo reboot[/COLOR]

before logging in, i clicked on settings and enabled GNOME

-same issue.. lol.. at this point i was getting really frustrated & was considering a re-install, but i decided to try one more thing..

i went back into synaptic (system / administration / synaptic packet manager) and did a search for KDE.. 
-then i clicked every KDE entry that had the Ubuntu logo next to it that seemed grapic / visual related.. in other words, i didn't bother with the stuff that looked like it was related to the educational programs. then i installed all those entries back into the system
-then i ran:

[COLOR="Navy"]sudo apt-get update
sudo apt-get upgrade
sudo reboot[/COLOR]

and to my suprise and utter relief, my customized desktop came up promptly & just as i had saved it!! i did some more customizations just to be sure.. saved & rebooted again.. desktop loaded up fast with correct settings.. i accessed the appearance options again.. no error

i have been running the computer consistently since last night with multiple reboots even logging into vista occasionally lol and have not seen the error one time. 

hope this helps someone.. i came to linux because i was tired of seeing constant errors & system slowdowns in windoze, i don't think anyone should have to settle for that in linux:D

i included a pic of my current desktop.. i had to scale it down a bit.. i'm running TwinView with my laptop screen at 1366x768 and my hdtv at 1360x768 for a combined resolution of 2726x768:guitar:

---

### Post by knlgSeekr on 2009-02-25
i was able to replicate and triple-replicate this issue.. and this time i did get a screenshot.. even thought i forgot to move the screenshot dialogue box away from the error lol.. but it will do.

so the exact error is:

Unable to start the settings manager 'gnome-settings-daemon'. Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may be active and conflicting with the GNOME settings manager.

now that i got the wording right, i did find a similar thread here [http://ubuntuforums.org/showthread.php?t=955679]("http://ubuntuforums.org/showthread.php?t=955679")
-that error however seemed to be related to an update libgstlibvisual.so, which is currently not listed in synaptic packet manager
and i also noticed that following that fix some people had to add the volume control back to their panel after the fix, and in their case the issue also affected pidgin.
-i had no issues with pidgin or my volume control disappearing

the issue definitely stems from an update, a kde related update to be exact.. which one exactly.. couldn't tell you.. i could've sat & messed with synaptic packet manager for a while & figured it out through a process of elimination but i didn't feel like it.. feel free to give it a try.

here is how i was able to consistently replicate the problem:

i ran:

[COLOR="Navy"]sudo apt-get update
sudo apt-get upgrade
sudo reboot[/COLOR]

what do you know, when the system rebooted.. my desktop was slow to load again and once my launchers had loaded on my panel, my theme settings disappeared & reverted to the default look. i clicked on launcher to change appearance settings (shortcut for system / preferences / appearance) and there was the error

so again, i went to synaptic packet manager, did a search for kde, highlighted everything that showed up, right-clicked & selected remove.. that took about a minute or 2 then it gave me verification prompt, i clicked yes, and all the kde related stuff was removed

then i ran:

[COLOR="Navy"]sudo apt-get remove kde
sudo apt-get autoremove kde
sudo reboot[/COLOR]

the desktop reloaded promptly without any errors.. i clicked on system / preferences / appearance.. no error message, everything was fine.. i was able to select my saved customized theme.. the only difference being that it was lacking the icons i had selected during customization which are part of the kde default packet. 

i rebooted the system about 3 times just to be sure, came up fine everytime.

so this time i decided to try something different.. lol
i ran:

sudo apt-get install kde

that took a while because it was installing everything kde related lol. once it was done, i rebooted & sure enough the error was back. 

so again i removed kde & all its dependencies & rebooted.. no error, system runs great

but i still wanted my kde related icons back & i do use pidgin so re-installed the necessary packets from source manager & everything is back to normal.. verified that by doing numerous reboots.. no issues

so.. this issue is definitely caused by a kde related update.. maybe later if i get bored i'll screw around & try to figure out which one it is.. like i said, i did a search for libgstlibvisual.so, that doesn't seem to be a currently available update. i currently have libsgutils1 installed, and thats the closest thing i could even find to that.

so if you come accross this problem, one sure fix is to get rid of the kde stuff & manually put back what you need.. provided you know what that is :smile:

---

### Post by whmitty on 2009-07-10
Another possible fix to try in addition to the above:

Although this issue is marked SOLVED I had this error recur after a major update to Ubuntu Hardy 8.04.2 in July '09 and along with the bootup error reported in these posts I took a major performance hit. Ultimately I booted into recovery mode and took a shot at running [COLOR=Blue]gnome-config[COLOR=Black] at the command line. The system reported that it was not installed so I issued the "sudo apt-get install gnome-config" command to install. After installation rather than even try running it I just rebooted. The gnome error message as described in these posts disappeared while the overall performance was back to normal. I didn't even have to run [COLOR=Blue]gnome-config[COLOR=Black].[/COLOR][/COLOR]
[/COLOR][/COLOR]

---

### Post by Ian Eales on 2009-12-24
Ubuntu 8.04 LTS x64
In the GUI : System / Adimistration / Connections

Unlock Wired Connection Properties disable Roaming and set Automatic Configuration DHCP.
this made the above changes to the hosts and interfaces files

---

