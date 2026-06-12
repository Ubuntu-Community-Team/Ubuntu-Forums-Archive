---
title: "BitTornado doesn't want to turn to green color"
date: 2006-02-25
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2006-02-25
So pretty much I can't download files like a normal person, it's stuck on yellow and that's that.

It all started around the time I installed firestarter. I'd like to know how I could open up some ports in firestarter in order to make this problem go away in firestarter. Anyone know how? Did anyone else have this problem? If so, how did you resolve it?

---

### Post by jon_gunnar on 2006-02-25
[QUOTE=YourSurrogateGod]So pretty much I can't download files like a normal person, it's stuck on yellow and that's that.

It all started around the time I installed firestarter. I'd like to know how I could open up some ports in firestarter in order to make this problem go away in firestarter. Anyone know how? Did anyone else have this problem? If so, how did you resolve it?[/QUOTE]

From another posting in this forum:
[http://ubuntuforums.org/showthread.php?t=132711&highlight=firestarter](http://ubuntuforums.org/showthread.php?t=132711&highlight=firestarter)

->Policy tab
->right-click on "allow service" and select "add rule"
->select "bittorrent" under name and it should open the ports for 6881-6889
->click "add" to finish.

---

### Post by YourSurrogateGod on 2006-02-25
[QUOTE=jon_gunnar]From another posting in this forum:
[http://ubuntuforums.org/showthread.php?t=132711&highlight=firestarter](http://ubuntuforums.org/showthread.php?t=132711&highlight=firestarter)

->Policy tab
->right-click on "allow service" and select "add rule"
->select "bittorrent" under name and it should open the ports for 6881-6889
->click "add" to finish.[/QUOTE]
I did that and restarted the BitTornado client, but it's still the same result. Do I need to re-boot?

---

### Post by taurus on 2006-02-25
It doesn't hurt to try to reboot to see if you still can connect with bittorent...

---

### Post by YourSurrogateGod on 2006-02-25
[QUOTE=taurus]It doesn't hurt to try to reboot to see if you still can connect with bittorent...[/QUOTE]
Didn't seem to have worked. I'm still stuck on yellow.

---

### Post by taurus on 2006-02-25
What if you disable firestarter and see if you can download with bittorent client!  If it turns to green, then you just have to look at your firestart's config;  On the other hand, if it still stays yellow, then there is something wrong with the client that you have and perhaps you should try another one.

---

### Post by YourSurrogateGod on 2006-02-25
[QUOTE=taurus]What if you disable firestarter and see if you can download with bittorent client!  If it turns to green, then you just have to look at your firestart's config;  On the other hand, if it still stays yellow, then there is something wrong with the client that you have and perhaps you should try another one.[/QUOTE]
It seems to be fine now. I've been having problems with my connection at the uni, I'll wait until Monday for someone to look into it. Thanks for the help.

---

### Post by taurus on 2006-02-25
Those IT techs can be pain in the neck sometimes...  :rolleyes:

---

### Post by YourSurrogateGod on 2006-02-25
[QUOTE=taurus]Those IT techs can be pain in the neck sometimes...  :rolleyes:[/QUOTE]
It's at an uni, what do you expect?

---

### Post by drachir on 2006-02-25
I have downloaded files many times and I would have to say that it has turned green about half the time.  Of course I dont stay watching the download to see if it changes but non the less I have recieved full download staying on yellow

---

### Post by YourSurrogateGod on 2006-02-26
[QUOTE=drachir]I have downloaded files many times and I would have to say that it has turned green about half the time.  Of course I dont stay watching the download to see if it changes but non the less I have recieved full download staying on yellow[/QUOTE]
Oh, I know that I can get a full download with yellow, it's just that it takes sooooooooooo much more time.

---

### Post by drachir on 2006-02-26
I quess I never noticed before. I setup my downloads right before I go to sleep and in the morning its like Christmas, and I open all my new downloads. \\:D/

---

### Post by YourSurrogateGod on 2006-02-26
[QUOTE=drachir]I quess I never noticed before. I setup my downloads right before I go to sleep and in the morning its like Christmas, and I open all my new downloads. \\:D/[/QUOTE]
Well, I have to be careful with that, since at my uni we have bandwith restrictions. So if I upload too much, I can be stuck with a 56k connection for a whole week and I don't even want to start imagining how bad that will suck.

I just shut off the firewall and everything seems to work fine. The only problem is that I don't feel too safe without my firewall :???: .

---

### Post by YourSurrogateGod on 2006-03-06
I can't believe I didn't think of this earlier. I simply set the ports of BitTornado to the ones that I prescribed in my firewall policy, restarted it and it works fine now. Oh well...

---

