---
title: "Gnome 3.4 Themes?"
date: 2012-04-06
forum: Desktop Environments
---

### Post by The_Autonomist on 2012-04-06
i've so far found one theme, Orion, that works with Gnome 3.4. 

WIll any of the older Gnome themes work? And if so, how do i install them? I'm new to Gnome 3...

---

### Post by zombifier25 on 2012-04-06
GNOME 3 themes designed for older versions like GNOME 3.2, etc. will not work correctly in 3.4. They works, but they will experience errors: [http://ubuntuforums.org/showthread.php?t=1940197](http://ubuntuforums.org/showthread.php?t=1940197)
Since GNOME 3.4 is still not default in most Linux distros, many theme makers hasn't come around to update them yet. So, you should wait :)

---

### Post by The_Autonomist on 2012-04-06
Thanks for the info. 

Well, if i DID want to try and install an older theme, just to see how it looks, how would i do that? I have Gnome Tweak, and gnome-shell-extensions. But, whenever i try and install gnome-shell-extensions-user-theme it tells me that it'll have to REMOVE gnome-shell-extensions and gnome-shell-commons. Then, it gives me an error message saying: 

> gnome-shell-extensions-user-theme:
 Depends: gnome-shell-extensions-common but it is not going to be installed

????

---

### Post by Frogs Hair on 2012-04-06
Besides the link I found a shell only theme (No GTK) . [https://launchpad.net/ubuntu/+source/gnome-themes-standard/3.4.0-0ubuntu1](https://launchpad.net/ubuntu/+source/gnome-themes-standard/3.4.0-0ubuntu1)

---

### Post by SwarSobieskiDN38416 on 2012-04-08
I am the developer of the Swar Themes. I have been studying the themes 'ported forward' for Gnome 3.4 and so far all I have seen is what appears to be completly new development of themes for Gnome 3.4 which are based on the old themes. I am still learning though so my skill is no where near where it needs to be for the tasks ahead as the Swar Themes were my first attempts at themes and any such work. 

The Gnome 3.4 themes appear to be the same theme but when looking at the code they are not! I am sad to say but I think all the old themes others and myself included developed are gone and we need to develop new themes based on the Gnome 3.0-3.2 themes to meet the new standards.

The problem therein is why should we as supporters of Gnome who gave our time for free get slapped in the face with new theme requirements and our work broken and failing to do more work at out own time to support something where the requirements could change again in another 6 months or less and again break our new work? It's a real pickle no doubts there!

This would be a continuing 'rat-race' to keep up and for myself I am running my own business and am also a step-in manager of a business for the full-time managers so I can not devote months on months to develop themes.

This said I am going to try to bring my work forward and I have been begging for help to learn or gain assistance but no one seems interested which is even more disheartening given the responses I received to the themes and how many people have downloaded them. I have taken all the work down and made 1 download for all to simplify everything so don't go by present counts.

For now the short and simple answer to your question based on my research, attempts and findings is the now 'old themes' will not work properly and if they are not redone then they are lost to time just like Gnome 2 and all the great themes for it. In the last week I have been trying to 'port my theme forward' and I have seen nothing other than the need to develop new themes based on the old themes.

---

### Post by Frogs Hair on 2012-04-08
There are few I discovered at Deviant Art. After installing 12.04 last night, I found that it is most important to have 3.4 shell theme or the icons won't display properly. I am currently using Elementary Luna 3.4 .

---

### Post by Frogs Hair on 2012-04-09
Here is a short list I have found so far. , Atolm is not working, but that may be a problem on my end .
GTK

Atolm
Orion 
Evolve
Aawaita Cupertino
Prophet-2
Eementary-mod-silver
Silver Improved
Majestic-3.4
elementary GTK 3.0

Shells 

London Smoke 
Elementary Lunu
Elegance

---

### Post by kiirokurisu on 2012-04-11
Thanks for the list Frogs Hair. Personally I've been using the default theme and Adwaita for several weeks, and they've actually grown on me so much that I probably won't change them... strange huh.

---

### Post by Frogs Hair on 2012-04-11
I have a couple of theme PPAS and I have been checking them daily. They are slowly being updated. I'm running 12.04 so I am sticking to 3.4 themes for Unity and the Gnome shell. I had some strange behavior while trying to use   3.2 themes. I can't wait to get a theme that is not gray and blue .

---

### Post by Dlambert on 2012-06-09
You can make 3.3 Themes work in 3.4 by modifying the css file to the settings: > .icon-grid {
    spacing: 36px; /* 36px */
    -shell-grid-horizontal-item-size: 118px; /* 118px */
    -shell-grid-vertical-item-size: 118px; /* 118px */
}

Source: [http://askubuntu.com/questions/126316/gnome-shell-issue-with-application-icons-using-themes](http://askubuntu.com/questions/126316/gnome-shell-issue-with-application-icons-using-themes)

---

