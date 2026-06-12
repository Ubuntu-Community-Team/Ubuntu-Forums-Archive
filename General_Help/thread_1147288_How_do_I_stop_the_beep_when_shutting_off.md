---
title: "How do I stop the beep when shutting off?"
date: 2009-05-03
forum: General Help
---

### Post by Cheater87 on 2009-05-03
This is getting quite annoying. i turn the volume down all the way till its muted and it still beeps. IIRC it only does it once. Is there something I can type in the terminal to cut the sound off?

---

### Post by linux_djc on 2009-05-03
Turn off sound under System -> Preferences > Power Management -> General -> Extras -> Sound notification.

---

### Post by internalkernel on 2009-05-03
linuxdjc's suggestion will work for Gnome sounds, but the console bell can be set with this command: 

```
setterm -bfreq 0
```

You can add that to /etc/profile to make it permanent. This will turn off the console bell completely, so no bells in any ttys.

---

### Post by Cheater87 on 2009-05-06
What do I put as /etc/profile?

---

### Post by internalkernel on 2009-05-07
Literally just that line... add it to /etc/profile - that is for system wide profiles. You can try adding it to your users profile in /home/user/.profile if you don't want to edit system files. 

You could, before you edit these files, try typing the setterm command in a terminal and then shutting down - if you get the desired result then edit the files (that will make it permanent). 

In a terminal... type:

```
sudo pico /etc/profile
```

Add this line to the very bottom:

```
setterm -bfreq 0
```

Hit Ctrl X, it will ask you to save - and then exit. This stops the system bell from going off in a console.

---

### Post by Cheater87 on 2009-05-09
I can't quite get it to work. Can you post a pic of what it will look like???

---

### Post by m4lte on 2009-05-09
> **Cheater87 said:**
> I can't quite get it to work. Can you post a pic of what it will look like???

- Open a terminal (Applications > Accessories > Terminal).

- Type 'sudo gedit /etc/profile'. When asked, enter your admin password.
This will open the text file profile in the text editor gedit.

- At the end of the text, add a line break and write 'setterm -bfreq 0'.
My file profile file looks like this, and yours should look similar:

```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022
setterm -bfreq 0
```
- Click 'Save' and close the text editor. The beep should now be disabled.

---

### Post by DougieFresh4U on 2009-05-09
Also 'gnome alsa mixer' has 'pc beep' you can mute

---

### Post by Cheater87 on 2009-05-20
Nope that terminal edit did not disable it.

---

### Post by milasch on 2009-05-20
> **DougieFresh4U said:**
> Also 'gnome alsa mixer' has 'pc beep' you can mute

No offense, but that's an ugly yellowish theme, isn't it? lol

---

### Post by dj-toonz on 2009-05-20
> **Cheater87 said:**
> This is getting quite annoying. i turn the volume down all the way till its muted and it still beeps. IIRC it only does it once. Is there something I can type in the terminal to cut the sound off?


The places are System / preferences , Sounds (disable all sounds) untick

System / Administration login window (enter password) accessibility (untick all boxes under sounds) then click ok

---

### Post by uupreti on 2009-05-20
> **Cheater87 said:**
> Nope that terminal edit did not disable it.

Try blacklisting your sound module. This worked for me.


```
 echo "blacklist snd_pcsp" >> /etc/modprobe.d/blacklist.conf 
```

---

### Post by Cheater87 on 2009-05-20
If I do that will I still have other sound like music and stuff come out?

---

### Post by internalkernel on 2009-05-21
I have no idea, blacklisting sound modules seems like a brutish hack in  my opinion. But, I see no other way. The terminal hack should fix it, though I noticed on mine I still have a beep when I shut down. Although, the terminal hack did stop the terminal beep from occuring which was annoying me more than the shut down beep... 

It's something I can live with... and, I'm out of ideas... sorry. 


@ milasch: couldn't agree more...

---

### Post by uupreti on 2009-05-21
> **Cheater87 said:**
> If I do that will I still have other sound like music and stuff come out?

yeah you can still get other sounds. In my case I can get music and other stuffs. It will only stop command error beep I guess. Try it once and you can always remove that line from file. It's not a problem.

---

### Post by Cheater87 on 2009-05-21
Turning off the sound in the sound options didn't work either.

---

### Post by mechdave on 2009-05-21
I tried this in the terminal--> xset b off that turned off the pc speaker and stopped from beeping when I fed it this test program -->

```

#include <iostream>
using namespace std;

int main()
{
	cout<<"\a";
	return 0;
}


```

to make it pernament I suggest you add it to the .bash_profile file in your $HOME directory eg: 

```
 echo xset b off >> .bash_profile 
```

Why I say your .bash_profile is so it won't affect other users (if any) and it is easy to remove if ever you want to reinstate the pc speaker

---

