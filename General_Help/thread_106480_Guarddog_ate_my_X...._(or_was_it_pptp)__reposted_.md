---
title: "Guarddog ate my X.... (or was it pptp?) _reposted_"
date: 2005-12-20
forum: General Help
---

### Post by unwoken on 2005-12-20
I have reposted this thread from:
[http://ubuntuforums.org/showthread.php?t=106236&highlight=guarddog+ate](http://ubuntuforums.org/showthread.php?t=106236&highlight=guarddog+ate)

in the hope that more people might see it here.  i will post there and point to this location if anyone has any suggestions.

any help will be very much appreciated.

.....................................

I was trying to connect properly to my VPN at work using pptp-linux, and followed the instructions from this thread:
[http://ubuntuforums.org/showthread.php?t=91249](http://ubuntuforums.org/showthread.php?t=91249)

everything installed fine, and i eventually was able to get the connection working after allowing a connection to the work IP in firewall.

unfortunately after a couple of minutes my entire internet connection would freeze, and even totally shutting pptp would not re-connect me.

i read further down in the thread listed above (post #10) that guarddog can help if you are having firewall problems with a VPN (which is what i assume(?) i was having).

so basically i loaded up synaptic and installed guarddog. i know it is supposed to be for KDE, but assumed that any relevant packages would be installed and i didn't really mind that.

i was surprised by the fact that only one package was installed by synaptic, but was not sure if that was an issue.

after reading that guarddog does not kick in until you configure it, i did so. directly after configuring it (i had 'exited' my firestarter icon from the tray) i attempted to open my 'sessions' option from the menu to disable firestarter on the next startup.

sessions did not load (crashed before properly opening), so i immediately logged out.

on attempting to re-log in to my user, X immediately crashed, giving me a message about the session lasting less than 10 seconds.

since then i have:
done an apt-get remove on guarddog from terminal
done a sudo dpkg --purge on guarddog
changed firestarter config from backup login (in the hope of overwriting any damaged config files from guarddog)
re-booted computer

X still crashes immediately on boot.

i am now in my backup user (glad i made one ) and am totally clueless as to what to do as i didn't change anything else.

i would REALLY appreciate some help as i certainly don't have any ideas (other than perhaps completely purging PPTP).

thanks in advance

uw.

...i will be happy to give more information if that is needed.

---

### Post by ccrab on 2005-12-21
I had a similar problem, X didn't crash but I got kicked out of gnome and back to the login prompt.  Your problem may be different.  

I fixed my problem logging in using failsafe mode and deleting the file .ICEAuthority as per [http://www.ubuntuforums.org/showthread.php?t=105184&highlight=ICEauthority]("http://www.ubuntuforums.org/showthread.php?t=105184&highlight=ICEauthority")

Using guarddog, and rebooting caused this problem for me.

---

### Post by unwoken on 2005-12-21
[QUOTE=ccrab]I had a similar problem, X didn't crash but I got kicked out of gnome and back to the login prompt.  Your problem may be different.  

I fixed my problem logging in using failsafe mode and deleting the file .ICEAuthority as per [http://www.ubuntuforums.org/showthread.php?t=105184&highlight=ICEauthority]("http://www.ubuntuforums.org/showthread.php?t=105184&highlight=ICEauthority")

Using guarddog, and rebooting caused this problem for me.[/QUOTE]

thanks ccrab.

somebody responded in the other thread i created (see link in my post above).  i had hoped to keep it all together, so apologies for the way it turned out, i did try to keep it together.

you were spot on.  it was the .ICEauthority file.  somehow the permissions got changed to 600, so i apparently did not have access when i tried to log in.  i just renamed it and could log in perfectly, as the system just created another one.

i 'think', although i can't really be 100% sure, that the problem was caused when i tried to run guarddog using the sudo command.  from what i have read, the command in kde is different and sudo can cause serious problems.

not really sure if i want to attempt using guarddog again after that, even if that was the problem.  i will try to access my work desktop some other way.

still, creating a second user was very helpful to me...

thanks again.

---

