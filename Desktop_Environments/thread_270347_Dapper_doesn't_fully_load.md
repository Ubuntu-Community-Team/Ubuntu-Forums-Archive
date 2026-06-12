---
title: "Dapper doesn't fully load"
date: 2006-10-03
forum: Desktop Environments
---

### Post by pwrstick on 2006-10-03
Strange things afoot...

When I boot Dapper everything seems to go fine all the way up to the Login/Password screen.  After I login, any of the following can occur, but nothing further happens afterwards:

[LIST=1]
[*]I get the brown background and a mouse cursor.  I can move the cursor.
[*]Brown background, mouse cursor, silver bars at the top and bottom of the screen with no icons.  No icons on the desktop.
[*]Brown Background, Cursor, Silver Bars, and some icons in the bars (i.e. Applications Places System ...) However nothing responds to clicking.
[*]Everything seems to load, and I even get items on the desktop that I can click on and open, but icons in the silver bars are inoperable.
[*]Everything loads perfectly fine and everything appears to be stable
[/LIST]

Now in any of those above options I can always do "alt-ctrl-1" and get a (fully?) working terminal.

The problem is that 'Everything loads perfectly fine' happens about 1 in 20 times.  I'm pretty confident that something is screwing everything up at boot so I'm hoping there's a way to look at a log and track down some bad app and remove it from init.d or rc2.d or whatever.

Thanks!
-Philip Smith

---

### Post by chrisccoulson on 2006-10-03
Have you tried logging in as another user to see if this a problem with your profile?

---

### Post by pwrstick on 2006-10-03
I just created a user (non superuser) and logged in perfectly fine with that new user.

Thank you for that suggestion -- I feel like I'm one step closer.  Now that it appears to be my profile, what can I do?

---

### Post by pwrstick on 2006-10-03
*bump*

---

### Post by pwrstick on 2006-10-03
So I turned the new user I created into an admin and now I'm just using that one.  The system works well enough, and I don't use it as an Ubuntu only system (more of an XP box), so even though I can function OK I'm very curious why it is doing what it's doing!

---

### Post by meatface on 2006-10-03
This sounds identical to an issue that I am having with Dapper. I solved it relatively the same way. But what I had to do was create a user in recovery mode and in the profile uncheck the sound priviledge. If I let any user have sound privileges, it will only boot once in a while. Uncheck the sound on any user and it boots fine. Does unchecking sound work for you?

Meatface

---

### Post by pwrstick on 2006-10-08
Yes!  So strange.  I wonder if we're using similar sound hardware.  I'd have to research what mine is on this HP Pavilion zx5000 laptop.  At first I thought just creating a new user did it, but slowly realized I had to remove the user from the sound group.  Now it always works.

Strange.

---

### Post by jhickey on 2006-11-14
I had to do the exact same thing to get 6.10 to load on my laptop (zx5000).  If I turn on sound 1 out of 10 times I will be able to login the rest of the time it hangs after I type my username and password.  

Has anyone found a solution to get sound working without locking up?

As a side note I installed SUSE 10.2 Beta 2 and had the same thing happen.  10.1 work fine (I used this before I switched to Ubuntu).

---

### Post by HazE_nMe on 2007-01-20
I was searching for a solution to my problem and I stumbled across this 3 month old topic and figured I would give it a bump. I am experiencing the exact same problem with my laptop (zx5000) and Dapper.  There is definately something wrong with sound using this laptop. How should users of this laptop help to get this problem resolved? Who should we get in touch with (alsa devs?)? I can provide any logs needed. Thanks in advance.

---

