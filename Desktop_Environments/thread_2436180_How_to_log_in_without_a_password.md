---
title: "How to log in without a password"
date: 2020-02-01
forum: Desktop Environments
---

### Post by arnaud-bidibulle on 2020-02-01
Hi,
I've installed Lubuntu 19.10 with FxQt. 
I'd like to create a user who can login without entering his password, just by clicking on his name. 
So far, I didn't find a way to do that. The option is grey (and not clickable) in the graphic interface and the command lines found on the internet don't work.
I'd really appreciate if someone could help me, thanks.

---

### Post by Dennis N on 2020-02-01
Read this post:
[https://ubuntuforums.org/showthread.php?t=2424761&p=13879631#post13879631](https://ubuntuforums.org/showthread.php?t=2424761&p=13879631#post13879631)
What happens if you add a 2nd user in the autologin section?

---

### Post by arnaud-bidibulle on 2020-02-01
> **Dennis N said:**
> Read this post:
[https://ubuntuforums.org/showthread.php?t=2424761&p=13879631#post13879631](https://ubuntuforums.org/showthread.php?t=2424761&p=13879631#post13879631)
What happens if you add a 2nd user in the autologin section?
I'm not looking for autologin. At the boot, I want to be able to choose between several users (it's a family computer): some users have to enter their password, others don't.
Edit: with one user in the sddm.conf file, the autologin works at the boot, with two users nothing happens: the password are asked for both users.

---

### Post by guiverc on 2020-02-01
Why not just use an empty (null) password?  (`passwd -d`  (or --delete))
I haven't tried it with `sddm`, but at worst it'll only require an enter key to be pressed I'm betting.

---

### Post by arnaud-bidibulle on 2020-02-01
> **guiverc said:**
> Why not just use an empty (null) password?  (`passwd -d`  (or --delete))
I haven't tried it with `sddm`, but at worst it'll only require an enter key to be pressed I'm betting.
When I write the command passwd -d user2, I have the following message: password expiry information changed
At the reboot, there is a change: I can't log in anymore in "user2" session, the password is refused and I can't log in with the enter key. I simply can't log in.

---

### Post by guiverc on 2020-02-01
> **arnaud-bidibulle said:**
> At the reboot, there is a change: I can't log in anymore in "user2" session, the password is refused and I can't log in with the enter key. I simply can't log in.

Sorry my testing way to weak so I apologize.  

On my 20.04 box I changed/erased the password of my 'blah' user (*used for testing*) using the `-d` and tested logging in only via text terminal (it worked).

I've now done the same on a 19.10 box and yes text login works as it did in my 20.04 test, however sddm isn't accepting login.  Sorry.

To fix, switch to text terminal, login, and then use `passwd` to change put a password back there so you can login via GUI. 

(I expected it to work, as we used empty passwords to login to 'live' sessions, but I'll have to explore if that was recent (whilst using LXQt) or my mind has gone to legacy (LXDE) days..  I'll provide more when I've explore some.)   Again sorry.

---

### Post by deadflowr on 2020-02-01
You need to uncomment the line
```
#auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
```
to read
```
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
```
in the file /etc/pam.d/sddm

Then add the user to the nopasswdlogin group.
If the group doesn't exist, create it.

Note that on login the password box stills shows, but you only need to click the Enter key.

---

### Post by guiverc on 2020-02-01
Thanks @deadflowr  :)

I didn't test that on 19.10 but on 20.04 it works.
20.04 doesn't have the line you mentioned, so I added it  (*update: or I'm to blind and didn't see the blue text on black background in default `vim` colors*)
I then `addgroup`, `usermod` & `systemctl` (restart sddm service) and 'enter' alone logs me in.

Thanks !

---

### Post by arnaud-bidibulle on 2020-02-02
> **guiverc said:**
> Sorry my testing way to weak so I apologize.  
Again sorry. No problem, we are here to test and try.

> **deadflowr said:**
> You need to uncomment the line
```
#auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
```
to read
```
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
```
in the file /etc/pam.d/sddm

Then add the user to the nopasswdlogin group.
If the group doesn't exist, create it.

Note that on login the password box stills shows, but you only need to click the Enter key.
For me, it doesn't work: I'm in my Windows7 session now: I can't log in anymore in any account in Lubuntu after modification of the /etc/pam.d/sddm and reboot.
 (user2 was correctly placed in the nopasswdlogin group, as I had already previously created the group and tried several commands found on the internet, without success)

---

### Post by guiverc on 2020-02-02
> **arnaud-bidibulle said:**
> No problem, we are here to test and try.


For me, it doesn't work: I'm in my Windows7 session now: I can't log in anymore in any account in Lubuntu after modification of the /etc/pam.d/sddm and reboot.


Can't you login to a text terminal (eg. ctrl+alt+f4) and change it back?

I'll boot a 19.10 & try what @deadflowr suggested there....
Back - it worked perfectly for me too in 19.10 ..

I'll add my commands
  ```
  217  20/02/02 17:38:31 sudo vim /etc/pam.d/sddm
  219  20/02/02 17:43:08 sudo addgroup nopasswdlogin
  221  20/02/02 17:43:50 sudo usermod -aG nopasswdlogin guiverc
```

I then logged out of GUI (used GUI so I could use `firefox` to read this site instead of `lynx`) then switched to term `sudo systemctl restart sddm`  (*not a fan of reboots*)  I'd erased my user password on text terminal earlier too, but those commands didn't show in my `history` run in GUI.

After reboot, a <Enter> had me login to gui.  I note however my `sudo apt update` failed to accept just <Enter> so possibly another policy prevents this, but I'll return to having a password instead of looking at why..

---

### Post by arnaud-bidibulle on 2020-02-02
> **guiverc said:**
> Can't you login to a text terminal (eg. ctrl+alt+f4) and change it back?

I'll boot a 19.10 & try what @deadflowr suggested there....
That's what I've done: I've booted in recovery mode and logged in root account: changed it back and saved.
Reboot: I can't log in in any account. Something is broken now.

---

### Post by guiverc on 2020-02-02
If you can't login to any account, my next *fallback* would probably be 'live' media (such as Ubuntu install media and selecting Start/Try Lubuntu/Ubuntu). 

It probably helps in that I have lots of numbered drives in front of me & a chart on the wall telling me what's on each numbered one..  (*used very often in testing..*)  But even before I was going *testing* I usually kept a *Knoppix* around to fix other peoples boxes[I].

[/I]At `grub` I'd remove the 'quiet splash' (possibly adding a '1' if needed or I didn't have 'live' media around) to I could see messages that I'd hope would provide a clue. 

If you're being logged pressing <Enter> at `sddm` and it appears to start login, then logs you out, it's not a system issue directly (config issue), so I'd expect terminal logins to still work. I'd login there and check disk space exists (`df` or disk free) as lack of space in $HOME or your user directory causes a GUI login to fail as it cannot create work-files needed for GUI without any warning/messages.

I would `diff` (*show differences*) your now /etc/pam.d/sddm with any backup you created (I create a file with date-appended when I make a change for easy back-out, plus leaving comments everywhere with dates and why changed) looking for errors, or start again.  If I forget all the places were I've made changes, I hope I can find it using `find -ctime`.  

Currently i'm not sure exactly where you're stuck,
Can you login using a text terminal?
Do you get to sddm? or has a change made to the sddm config file caused it to not work?
If sddm appears, do it look like it logs in & then loops?  (ie. no disk space issue like problem)
or something different?

---

### Post by deadflowr on 2020-02-02
Did you remount the file system read/write in recovery mode?
If so, how: what command?

---

