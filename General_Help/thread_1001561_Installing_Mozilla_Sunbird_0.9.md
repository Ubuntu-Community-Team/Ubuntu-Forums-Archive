---
title: "Installing Mozilla Sunbird 0.9"
date: 2008-12-04
forum: General Help
---

### Post by MeanStreak on 2008-12-04
Hi,

I want to install Sunbird 0.9. This is the version required if I wish to then install the Google calendar provider meaning I can then sync Sunbird with my Google Calendar (Thunderbird on my Windows box at work can do this with Lightning, not so easy in Ubuntu-land).

Any help would be appreciated.

---

### Post by Asgar on 2008-12-04
Whats sunbird?

---

### Post by Aearenda on 2008-12-04
Sunbird is the standalone calendar from Mozilla (like Firefox & Thunderbird).
I use Sunbird 0.9. If I remember correctly, I installed it by...

1. Download the Linux version from [http://www.mozilla.org/projects/calendar/sunbird/](http://www.mozilla.org/projects/calendar/sunbird/)
2. Move the file to a suitable spot and extract it:
```
cd /opt
sudo mv <where-it-is-now/the-downloaded-file> ./
sudo tar -xzvf <the-downloaded-file>

```

3. I added a link to it in /usr/local/bin so I could start it just by typing 'sunbird':```

sudo ln -s /opt/sunbird/sunbird /usr/local/bin/
```

4. I used the menu editor to create a menu item pointing to 'sunbird' and using the icon at /opt/sunbird/icons/mozicon128.png.

Read [http://www.mozilla.org/projects/calendar/releases/sunbird0.9.html](http://www.mozilla.org/projects/calendar/releases/sunbird0.9.html) about timezones.
That's it!

BTW, what didn't work for you with Lightning on Ubuntu?

---

### Post by Reno II on 2008-12-10
Hi,

I solved the installation problem with the .deb package: 

[http://www.getdeb.net/app/Sunbird](http://www.getdeb.net/app/Sunbird)

rouge_ronin posted this link: [http://ubuntuforums.org/showthread.php?t=996097&highlight=sunbird](http://ubuntuforums.org/showthread.php?t=996097&highlight=sunbird)

Thanks Aearenda for your nice post,

---

### Post by deadowl on 2008-12-10
Ugh... after all I went through trying to get GCalDaemon to work with Evolution since its Google Calendar support sucks.

---

