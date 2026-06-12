---
title: "gnome-terminal ssh-add fails in session startup"
date: 2006-11-24
forum: Desktop Environments
---

### Post by adamthetownkrier on 2006-11-24
Hello,

I am trying to automate adding my ssh keys to my ssh agent on gnome login. They all have passphrases that I have to type in once when i add them, but I want it to automatically pop up windows for each of them prompting me for my passphrase at startup. So what i did was i added the following commands to my System-> Preferences-> Sessions -> Startup Programs:
gnome-terminal --title=Helios -x ssh-add ~/.ssh/helios_ossh.priv 
gnome-terminal --title=ATTK.noip -x ssh-add ~/.ssh/attk_noip_ossh.priv 
gnome-terminal --title=Geesu -x ssh-add ~/.ssh/geesu_ossh.priv 

Now... nothing flippin happens at startup! If i copy one of those commands and enter it into a terminal, it does exactly what I want: it pops up a gnome-terminal that says (for instance):
Enter passphrase for /home/adam/.ssh/attk_noip_ossh.priv:


However! It doesn't do anythign at session startup! what the heck!

Any assistance or perhaps different ways to automate adding my keys to my ssh agent all would be appreciated

Thanks,
attk

---

### Post by bkeithly on 2006-12-18
Did you ever figure this out?

I know it can be done before starting X.  I use this process with Freebsd, but I am looking for a method to get it to work with ubuntu.

Please let me know if you figure this out.

---

### Post by adamthetownkrier on 2006-12-19
No I never heard anything and never figured it out myself. I tried switching around some of the gnome-terminal arguments but still nothing worked..

The weirdest part is taht when gnome starts i can see a window pop up for a split second, as if the command is going to work, but then the window disappears never to be seen again...

Let me know if you are able to find anything out.

---

### Post by alex.knk on 2007-02-07
I done it that way:
vi /etc/X11/Xsession.d/90x11-common_ssh-agent

comment 3 lines at the end of file
[I]
#if [ -n "$STARTSSH" ]; then
#  STARTUP="$SSHAGENT $SSHAGENTARGS $STARTUP"
#fi
[/I]
then add to the end of file
[I]
eval `$SSHAGENT`
ssh-add /home/user/.ssh/key
[/I]

---

