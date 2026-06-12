---
title: "Clear recent documents -- Ubuntu Unity"
date: 2011-01-29
forum: Desktop Environments
---

### Post by kill4killin on 2011-01-29
Ok so not to make he back story too long, as I tend to do ( jump to next paragraph for my question), I just setup a media center PC for my living room with Ubuntu 10.10 and I'm running XBMC as the media center interface which is really nice because the buttons and everything are nice and big and visible from my couch for someone as blind as I am. Gnome, however, is not so easy to see, I tried increasing the font sizes which helped for some things but for things like the open and close buttons and the text under desktop icons were all still very small so I thought that I would try out Unity on the media center. I am very impressed with it overall, while you can definitely tell that it's in development it runs well and looks clean. But now on to my question.

The only thing that I can say that I absolutely don't like is that there is no obvious way to remove the recent files from the "recent" section under the files and folders menu. I have tried the rm -f ~/.recent-used.xbel trick that I've seen around on many forum posts. While that seems to have prevented new items from being added there is still one item on there and I don't want it. Does anyone know where this information is stored so I can clear it whether manually or via some menu that's hidden somewhere?

Thanks

---

### Post by kill4killin on 2011-01-30
bump  \\:D/

---

### Post by Gold3nBoy on 2011-02-13
I am also wondering the same. I tried ubuntu tweak, but no luck.

---

### Post by mutifo on 2011-02-21
```
rm ~/.local/share/zeitgeist/activity.sqlite
zeitgeist-daemon --replace
```

---

### Post by mutifo on 2011-02-21
if you want to prevent new items from being created do the following:

```
echo -n > ~/.recently-used.xbel
sudo chattr +i .recently-used.xbel
```

if you change your mind just do:
```
sudo chattr -i .recently-used.xbel
```

---

### Post by phonicboom on 2011-04-10
> **kill4killin said:**
> The only thing that I can say that I absolutely don't like is that there is no obvious way to remove the recent files from the "recent" section

Not tried this but how about going to startup items and turning off the zeitgeist feature then logging back in. 

When development settles, perhaps even now, their should be a simple enough way to edit out the file lense so it does not even show in the unity launcher.

---

### Post by Issssy on 2012-01-25
It would be nice if there was a way in the Unity UI to do this (other than command line). I don't want to turn it off, but I do like to periodically clear it.

---

### Post by Krytarik on 2012-01-25
> **Issssy said:**
> It would be nice if there was a way in the Unity UI to do this (other than command line). I don't want to turn it off, but I do like to periodically clear it.
It *is*; if running Oneiric 11.10, simply install "Activity Log Manager" from the official repos; if Natty 11.04, please see this guide:

[http://www.tuxgarage.com/2011/05/clear-tweak-zeitgeist-historys-settings.html](http://www.tuxgarage.com/2011/05/clear-tweak-zeitgeist-historys-settings.html)

Regards.

---

### Post by Issssy on 2012-01-27
I am running 11.10.

I down-loaded and installed it (search for the full string in the software manager -- activity-log-manger).

Ran it and deleted the last week of history. Went to recent docs in Dash and they were still there. I re-booted, and they were gone. I assume you have to re-boot to get the deletion to take?

File names are still there in movie player...   does it maintain its own list?

---

### Post by Krytarik on 2012-01-27
> **Issssy said:**
> I down-loaded and installed it (search for the full string in the software manager -- activity-log-manger).

Ran it and deleted the last week of history. Went to recent docs in Dash and they were still there. I re-booted, and they were gone. I assume you have to re-boot to get the deletion to take?
May it be that you didn't restart the Zeitgeist daemon after installing Activity Log Manager?

Otherwise, restarting it after clearing the history should be sufficient; via Alt+F2, run:
```
zeitgeist-daemon --replace
```> **Issssy said:**
> File names are still there in movie player...   does it maintain its own list?
Yep, most apps do that.

---

### Post by Issssy on 2012-01-27
Totem Movie Player pulls its recent files from Recent Documents; not its own list.

[http://www.howtogeek.com/howto/ubuntu/clear-history-from-totem-movie-player-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/clear-history-from-totem-movie-player-in-ubuntu/)

Does the zeitgeist daemon actually clear the Recent  Documents list, or is the list now "orphaned" in Unity? Is there a synchronization bug here?

---

### Post by Krytarik on 2012-01-27
> **Issssy said:**
> Totem Movie Player pulls its recent files from Recent Documents; not its own list.
Yeah, you are right, I didn't take the old global "Recent Documents" infrastructure into account; to clear that data, run:
```
rm ~/.local/share/recently-used.xbel
```> **Issssy said:**
> Does the zeitgeist daemon actually clear the Recent  Documents list, or is the list now "orphaned" in Unity? Is there a synchronization bug here?
As you can see, there are currently two activity logs running parallelly: the old "Recent Documents" system, which is still being used by most apps; and the new Zeitgeist system. So to clear *all* log data, you need to clear both of them.

Btw., please notice my latest edit to my previous reply: did you restart the Zeitgeist daemon before using the Activity Log Manager, clearing your history?

---

### Post by Issssy on 2012-01-27
I did. I'll run some tests and try it. Thank you!

---

