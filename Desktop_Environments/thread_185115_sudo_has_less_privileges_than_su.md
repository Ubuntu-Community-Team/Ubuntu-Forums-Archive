---
title: "sudo has less privileges than su?"
date: 2006-05-31
forum: Desktop Environments
---

### Post by Sukarn on 2006-05-31
I had to run this command to be able to get sounds in "return to castle wolfenstein: enemy territory". The command to run enemy territory is "et".
```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```
Running this command with sudo gives "Permission denied" but if I log into root with the su command, I can run the above mentioned command without any errors. This makes me wonder whether sudo has lesser privileges than root.
Any comments?
I got the sound fix from the first post at - [http://www.ubuntuforums.org/showthread.php?t=5246](http://www.ubuntuforums.org/showthread.php?t=5246) who had obtained that fix from - [http://alsa.opensrc.org/index.php?page=FAQ023](http://alsa.opensrc.org/index.php?page=FAQ023)

---

### Post by hw-tph on 2006-05-31
It's a redirection issue. sudo doesn't handle redirection - your shell does.

The superuser shell (sudo) runs the echo command with root privileges, and then your own shell - with regular user privileges - tries to open /proc/asound/card0/pcm0p/oss and write the result of the echo command.

One solution to this is sudoing a complete shell: **sudo sh -c 'echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss'**
This is a bit cumbersome though. Just use **sudo -i** to get a real root prompt (with $USER and everything else set to root - yes, it will fool the nvidia installer and other programs, no need to set a root password).


Håkan

---

### Post by Sukarn on 2006-05-31
Before I realised that we could use root account with "sudo -i" I had already created a password for the root account.

I am relatively new to linux (I guess you guys hear this all over the forum), and I think that is what led to the ignorance and foolishness of not having thought of using the complete shell under single parenthesis.

Thanks hw-tph, I think my script should work now (I had created a script for launching enemy-territory). The script included the above mentioned command followed by execution of the game (with gksudo instead of sudo). I had tried it with shell however and that was the part that I was asking help for.

**EDIT:** Yes, its working. I can hear the sounds.

---

### Post by hw-tph on 2006-05-31
Glad to hear you got it working at last.

[QUOTE=Sukarn]I am relatively new to linux (I guess you guys hear this all over the forum), and I think that is what led to the ignorance and foolishness of not having though of using the complete shell under single parenthesis.[/QUOTE]

I didn't mean to jump on you for not knowing this, not at all. I have had my own share of headaches relating to sudo and shell redirection very recently, that's how I knew the answer. :)


Håkan

---

### Post by Sukarn on 2006-05-31
No wait, it seems that the sound was working because I had passed that command in shell (to test it) before I put it in my script.
The command needs to be run everytime the computer is restarted for the sounds to work.
I am attaching a copy of the script here, please tell me if I am doing something wrong -

```
gksudo 'echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss';
gksudo /usr/local/games/enemy-territory/et
```

**EDIT : ** Seems that I was trying to run the command without ***sh -c***, and that was why it was not working.

---

### Post by Sukarn on 2006-05-31
```
gksudo sh -c 'echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss'
gksudo /usr/local/games/enemy-territory/et #"+set fs_game tcetest"
```
still doesn't work. I had to resort to the following and making it "Run in Terminal" to make it work. Yeah, it works perfectly in terminal.
```
sudo sh -c 'echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss'
sudo /usr/local/games/enemy-territory/et #"+set fs_game tcetest"
```

---

