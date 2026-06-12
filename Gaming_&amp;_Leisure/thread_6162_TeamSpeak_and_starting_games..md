---
title: "TeamSpeak and starting games."
date: 2004-11-25
forum: Gaming &amp; Leisure
---

### Post by FX on 2004-11-25
First off I was thinking maybe we need a seperate forum for gaming issues/news and the likes.

Second I have TeamSpeak installed and ET: TrueCombat:Elite mod. If I try to run the two or better if I start TeamSpeak, Elite won't start. I think its a sound driver issue with both programs wanting to use sound. I've done some searching on Google for an answer and from what I see I pretty much have to jump through hoops of fire to get them working together. I just want to know why? I wouldn't have this problem in M$ and I really would rather not use M$, but until Linux can get this straight without being a guru I have no choice!!

This is both a "help me" and complain/whine thread.  :D

Any help would be nice.

FX

---

### Post by jdong on 2004-11-25
we do have a gaming forum!

---

### Post by FX on 2004-11-25
Oppps! Sorry I see that now that its a "sub-forum". I guess this would call for a move of the thread?  :D

FX

---

### Post by wezzer on 2004-11-28
Hi!

I had problem with this also, but asking from Google helped. Type to your terminal these commands:

```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```
```
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
```

Best regards,
Wezzer

---

### Post by FX on 2004-11-30
joe@laptop:~ $ sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
bash: /proc/asound/card0/pcm0p/oss: Permission denied

Thanks for the help, but again another snag. Trust me I love linux, but with things like this it will be a while before it can go main stream. People are not going to want to do this just to play games and run voice chat at the same time. Especially when you still get errors or "permission denied".

FX

---

### Post by tymark on 2004-11-30
what are the permissions on /proc/asound/card0/pcm0p/oss ?  sounds like it's not writable, hence the permission denied error ;)

---

### Post by FX on 2004-11-30
joe@laptop:~ $ ls -l  /proc/asound/card0/pcm0p/oss
-rw-r--r--    1 root     root            0 2004-11-30 18:55 /proc/asound/card0/pcm0p/oss


If I'm not mistaken I believe it is root. Hence the sudo command before I tried to 'echo",unless I am missing something blaring obvious. 

FX

---

### Post by crane on 2005-01-04
[QUOTE=FX]joe@laptop:~ $ ls -l  /proc/asound/card0/pcm0p/oss
-rw-r--r--    1 root     root            0 2004-11-30 18:55 /proc/asound/card0/pcm0p/oss


If I'm not mistaken I believe it is root. Hence the sudo command before I tried to 'echo",unless I am missing something blaring obvious. 

FX[/QUOTE]
 I just tried this command as well with the same errors?
 anyone have any idea?

---

### Post by crane on 2005-01-07
OK I found something on this problem.

I entered the two commands above and recieved "permission Denied"
Then I entered them again with the sudo command and still no luck.

After this I enabled root accout using this command -->sudo passwd root.
entered old password, then entered new password. This enabled me to either completely switch to root or even log in as root if I so wished.

 So I switched to root ( su command) enter password prompt changed from $ to # as it's supposed to. 
Now I enter the command and BOOM, no errors. :D 

So in short, you have to enable root access and actually be root to use the commands above!

Hope this helped some one!!

---

### Post by WegDamit on 2005-06-03
Use the fllowing line to do it with sudo:

 sudo  sh -c 'echo "et.x86 0 0 disable" > /proc/asound/card0/pcm1c/oss'

the before mentioned command  does the echo as root, but the redirect as the normal user.  [-X 

And this command gives me on my AC97 Board still no sound. ](*,) 
But et didnt hang at "sound initilization" any more.  

Any more hints?

---

### Post by rutty on 2005-06-25
This is all doing my head in too. Why is it so hard to get it to work?  ](*,)

---

