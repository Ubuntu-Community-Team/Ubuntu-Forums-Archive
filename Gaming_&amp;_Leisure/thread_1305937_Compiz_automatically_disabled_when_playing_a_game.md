---
title: "Compiz automatically disabled when playing a game"
date: 2009-10-30
forum: Gaming &amp; Leisure
---

### Post by phoozle on 2009-10-30
Just thought I'd share my little creation with the Ubuntu community.

You basically define what games or software the script should look for and if it finds that one is running it will switch the window manager to Metacity. When the game is no longer running the script switches the window manager back to Compiz.

I made this script because I got sick of having to do it manually via Compiz Fusion Icon.

Hope someone finds this useful :D

---

### Post by Bölvaður on 2009-11-01
this is cool, going to look through the script later today and see how you made it.
I dont need it my self but I can see that others might

---

### Post by 5nak3 on 2009-11-02
This sounds like something I would like to try out actually, but I was wondering how exactly do you use it.

I haven't downloaded it (not at home at the moment) so I've not been able to look at what is included in the file. I would like some information tho if possible. When you set up the script with the individual games, do you have to run the script first and then the game or does the script run in the background all the time?

---

### Post by Duskao on 2009-11-03
I am about to try this, will it work with all games or will I have to change certain things with different games? like prey.exe?
Fantastic idea btw. Great work.

---

### Post by Duskao on 2009-11-03
Had to do a new reply cause edit wouldn't work. With this script, it's checking every 5 seconds, thats great, but the problem is that even in game it's checking every 5 seconds and it actually crashed my game because of this. Any thoughts, maybe a fix or work around?

---

### Post by phoozle on 2009-11-04
**I encourage you all to download the latest version as I've made a few modifications. I've re-uploaded to my original post. **
[http://ubuntuforums.org/attachment.php?attachmentid=134661&d=1257335634](http://ubuntuforums.org/attachment.php?attachmentid=134661&d=1257335634)
Delete your old game-detect and install the new one to ensure nothing conflicts.
Be sure to run the following command to take advantage of the new notification functionality in v2.```
sudo apt-get install libnotify1
```

Answers to your questions:
Q: Does the script run in the background all the time?
A: Yes, as long as you follow the install guide that comes with the script. It is configured on a per-user basis.

Q: Will it work with all games or will I have to change certain things with different games? like prey.exe?
A: It will work with all games but yes you have to configure it your self. Just add prey.exe to the config file. Though in version 2 I've added it for you :P

Q: Help! Your script crashes my game!
A: Sadly I don't have a fix for this. I have only tested my script with Counter Strike Source which doesn't seem to mind my script changing the window manager. Try increasing the check time to 10 or 20 seconds. If you are willing to help me debug this please contact me: phoozle <at> gmail *d0t* com

---

### Post by Duskao on 2009-11-07
Giving the new one a try on karmic 9.10. I'll let you know how it goes once I install a few games and test them.

---

