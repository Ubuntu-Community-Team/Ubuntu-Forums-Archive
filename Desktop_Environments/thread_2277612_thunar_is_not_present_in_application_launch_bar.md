---
title: "thunar is not present in application launch bar"
date: 2015-05-10
forum: Desktop Environments
---

### Post by rom117 on 2015-05-10
I am using Lubuntu 14.04. I just installed thunar:
```
sudo apt-get install thunar
```
I want to set it in my launch bar: right click on panel -> panel settings -> panel applets (see [COLOR=#000000]panel_preferences.png).
[/COLOR]Then I select Application Launch bar and click on Preferences.
It opens the application launch bar (see [COLOR=#000000]application_launch_bar.png). 
[/COLOR]I unfold Accesories and now I want to select Thunar but it is not present! :(. There is PCManFM and Nautilus (Files) though...
From the menu, I do see it in Accessories and can open it!

Is it a bug?

---

### Post by kunitoki2 on 2015-05-10
Weird.
Maybe you can make Thunar appear this way:
Remove the Launch Bar from the Panel.
Now open the text file /.config/lxpanel/Lubuntu/panels/panel (the .config folder is in your home folder and it's hidden).
Now look for this section (it can look different here and there on your system):

Plugin {
    type = launchbar
    Config {
        Button {
            id=/usr/share/applications/pcmanfm.desktop
        }
    }
}

and make it look like this (I mean just add a button section for Thunar):

Plugin {
    type = launchbar
    Config {
        Button {
            id=/usr/share/applications/pcmanfm.desktop
        }
        Button {
            id=/usr/share/applications/thunar.desktop
        }
    }
}

Now add the Launch Bar to the Panel again and hope Thunar appears now.

---

### Post by vasa1 on 2015-05-10
> **rom117 said:**
> I am using Lubuntu 14.04. I just installed thunar:
...
 There is PCManFM and Nautilus (Files) though...
...
Is it a bug?

I feel that having PCManFM, Thunar, and Nautilus all on the same system could possibly introduce complications.

---

### Post by rom117 on 2015-05-10
> **kunitoki2 said:**
> 

Now open the text file /.config/lxpanel/Lubuntu/panels/panel (the .config folder is in your home folder and it's hidden).

Plugin {
    type = launchbar
    Config {
        Button {
            id=/usr/share/applications/pcmanfm.desktop
        }
        Button {
            id=/usr/share/applications/thunar.desktop
        }
    }
}


Unfortunately it did not work :(.
But I have found the problem: I had installed alacarte to edit my menu and it was hiding Thunar. I am not sure it was the root of the problem since I could see it from the menu but once I unistalled it, I could access Thunar from the application Launch bar.
Now when I looked at the file /home/[username]/.config/lxpanel/Lubuntu/panels/panel I see:
```
Plugin {
  type=launchbar
  Config {
    Button {
      id=menu://applications/Accessories/Thunar.desktop
    }
    Button {
      id=/usr/share/applications/chromium-browser.desktop
    }
    Button {
      id=/usr/share/applications/lxterminal.desktop
    }
  }
}

```

Thank you [COLOR=#000000]kunitoki2 :).

Problem solved![/COLOR]

---

### Post by rom117 on 2015-05-10
> **vasa1 said:**
> I feel that having PCManFM, Thunar, and Nautilus all on the same system could possibly introduce complications.
You're right I guess...
I installed Nautilus for the extension to mass rotate and resize images.
I installed Thunar cause PCManFM often crashes on my system. If I am satisfied with Thunar and find a similar extension, I will uninstall both PCManFM and Nautilus :)

---

### Post by markf2 on 2015-05-10
> **rom117 said:**
> I unfold Accesories and now I want to select Thunar but it is not present! :(. There is PCManFM and Nautilus (Files) though...
From the menu, I do see it in Accessories and can open it!

Is it a bug?

For what it's worth, I had the same problem with Chromium web browser after installing it via the Lubuntu Software Center. It appeared in the system menu but not in the task bar tool to add an application launcher to the task bar.

It ended up appearing after 3-4 days. I don't know what I did. The only thing I can think of is that I edited an unrelated .desktop file so it wouldn't display (it was an import function that installed with Rainlendar). Maybe that edit caused the task bar feature to refresh itself in a way the Chromium install didn't?

---

