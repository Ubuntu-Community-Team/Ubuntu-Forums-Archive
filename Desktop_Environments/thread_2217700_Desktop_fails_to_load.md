---
title: "Desktop fails to load"
date: 2014-04-18
forum: Desktop Environments
---

### Post by warner2 on 2014-04-18
Hi,

after upgrading to 14.04, my nvidia driver did not start. After some updating and re-installing drivers, the login screen starts as expected, but as soon as I type the password, I get "system problem detected". Lightdm is still working, the screen does not turn black, but nothing further happens. 

So far I tried:
 - removing all NVIDIA drivers (which got me to the above situation, with the system booting until the login screen)
 - installing gnome as alternative, to see if the problem was with unity (nope: same result)
 - installing gdm and making it the default over lightdm (nope: no change)

Now I'm lost.. what shall I try next? Which logs shall I read and what to look for?

Thanks for any help.

Warner

---

### Post by warner2 on 2014-04-18
Some additional info: 

reading /var/log/lightdm/lightdm.log, I'm seeing:

[+22.23s] DEBUG: Session pid=3194: Got 1 message(s) from PAM
[+22.23s] DEBUG: Session pid=2828: Prompt greeting with 1 message(s)
[+22.23s] DEBUG: Session pid=2828: Greeter start authentication for warner
[+22.23s] DEBUG: Session pid=3194: Sending SIGTERM
[+22.23s] DEBUG: Session pid=3194: Terminated with signal 15
[+22.23s] DEBUG: Session: Failed during authentication
[+22.23s] DEBUG: Seat: Session stopped

Can this be what's going wrong?

---

### Post by warner2 on 2014-04-18
Additional comment: seems to be same problem as [**[COLOR=#000000]Manoj_Kumar_Sakarw[/COLOR]**]("http://ubuntuforums.org/member.php?u=1917320") is having, below. Tried all suggested solutions, to no avail. 

Any help is appreciated!

---

### Post by warner2 on 2014-04-18
Another update: 

Installed KDE, and it turns out that this is running fine (no, now reporting from my workstation again :)). The "system problem detected"  was coming from apport, with a message related to x (but that might well be from the nvidia driver failing earlier). Now there are no more error messages, but the result (in Unity and Gnome) is still the same: I'm seeing my background picture and the mouse pointer and other than this, nothing.

Then, I tried:
> 
sudo dpkg-reconfigure compiz


And got:
> 
/var/lib/dpkg/info/compiz.config: 1: /var/lib/dpkg/info/compiz.config: [general]: not found
/var/lib/dpkg/info/compiz.config: 2: /var/lib/dpkg/info/compiz.config: backend: not found
/var/lib/dpkg/info/compiz.config: 3: /var/lib/dpkg/info/compiz.config: plugin_list_autosort: not found
/var/lib/dpkg/info/compiz.config: 5: /var/lib/dpkg/info/compiz.config: [gnome_session]: not found
/var/lib/dpkg/info/compiz.config: 6: /var/lib/dpkg/info/compiz.config: backend: not found
/var/lib/dpkg/info/compiz.config: 7: /var/lib/dpkg/info/compiz.config: integration: not found
/var/lib/dpkg/info/compiz.config: 8: /var/lib/dpkg/info/compiz.config: plugin_list_autosort: not found
/var/lib/dpkg/info/compiz.config: 9: /var/lib/dpkg/info/compiz.config: profile: not found
/var/lib/dpkg/info/compiz.config: 11: /var/lib/dpkg/info/compiz.config: [general_ubuntu]: not found
/var/lib/dpkg/info/compiz.config: 12: /var/lib/dpkg/info/compiz.config: backend: not found
/var/lib/dpkg/info/compiz.config: 13: /var/lib/dpkg/info/compiz.config: integration: not found
/var/lib/dpkg/info/compiz.config: 14: /var/lib/dpkg/info/compiz.config: plugin_list_autosort: not found
/var/lib/dpkg/info/compiz.config: 15: /var/lib/dpkg/info/compiz.config: profile: not found


Any ideas what to do?

---

