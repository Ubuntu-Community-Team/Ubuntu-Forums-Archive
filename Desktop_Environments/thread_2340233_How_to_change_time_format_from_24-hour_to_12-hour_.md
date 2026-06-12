---
title: "How to change time format from 24-hour to 12-hour via the terminal?"
date: 2016-10-16
forum: Desktop Environments
---

### Post by jdo300 on 2016-10-16
Hello All,

I have several systems that I am installing Ubuntu 14.04 LTS but would also like to include the lubuntu desktop environment as an option for users. However, the default time format is in 24-hour time rather than 12-hour time. I know how to manually change it through the GUI but how can I change it using the command line? I am working on a bash script to setup the systems and would like to automate the process.

Thanks,
Jason O

---

### Post by oldrocker99 on 2016-10-17
Try this:```
date +%r
```

---

### Post by jdo300 on 2016-10-17
> **oldrocker99 said:**
> Try this:```
date +%r
```

Hi, Thank you for the tip. Unfortunately, this didn't appear to change anything for the system, but just printed the formatted time to the termrinal window.

What I would like to do is change the system clock time format from %R to %I:%M %p. I also tried: ```
date +%I:%M %p
```, but this just gave me the error: "date: extra operand '%p'" Then I took the %p off just for grins and again, it just printed the date to the terminal without changing the system time format. Is there something I'm missing?

- Jason O

---

### Post by CantankRus on 2016-10-18
You need to enclose in quotes when running in terminal and spaces are involved...
```
date '+%I:%M %p'
```
It does nothing but print out the date according to format given. 
To change the system date format I think you may have to use "locale" which I know little about and don't like to mess with.
[**_[COLOR="#B22222"]How to change date formats on Ubuntu[/COLOR]_**]("https://ccollins.wordpress.com/2009/01/06/how-to-change-date-formats-on-ubuntu/")

If you just want to change the format of the lxpanel clock you could create a config file, **~/.config/lxpanel/Lubuntu/panels/panel**
There is no ~/.config/lxpanel/Lubuntu/panels/panel file until a user changes a panel setting. Default settings come from /etc/xdg/lxpanel/default/panels/panel 
When you change a panel setting a **~/.config/lxpanel/Lubuntu/panels/panel** file is created.

eg: Testng from a live Lubuntu ISO, this **~/.config/lxpanel/Lubuntu/panels/panel** config was created after changing the clock using GUI.
Near the bottom is the [COLOR="#FF0000"]new date format[/COLOR] for dclock.
```
# lxpanel <profile> config file. Manually editing is not recommended.
# Use preference dialog in lxpanel to adjust config when you can.

Global {
  edge=bottom
  allign=left
  margin=0
  widthtype=percent
  width=100
  height=24
  transparent=0
  tintcolor=#000000
  alpha=0
  setdocktype=1
  setpartialstrut=1
  usefontcolor=1
  fontcolor=#000000
  background=0
  backgroundfile=/usr/share/lxpanel/images/lubuntu-background.png
  iconsize=24
}
Plugin {
  type=menu
  Config {
    image=/usr/share/lubuntu/images/lubuntu-logo.png
    system {
    }
    separator {
    }
    item {
      command=run
    }
    separator {
    }
    item {
      image=gnome-logout
      command=logout
    }
  }
}
Plugin {
  type=launchbar
  Config {
    Button {
      id=pcmanfm.desktop
    }
    Button {
      id=lxde-x-www-browser.desktop
    }
  }
}
Plugin {
  type=space
  Config {
    Size=4
  }
}
Plugin {
  type=wincmd
  Config {
    Button1=iconify
    Button2=shade
  }
}
Plugin {
  type=space
  Config {
    Size=4
  }
}
Plugin {
  type=pager
  Config {
  }
}
Plugin {
  type=space
  Config {
    Size=4
  }
}
Plugin {
  type=taskbar
  expand=1
  Config {
    tooltips=1
    IconsOnly=0
    AcceptSkipPager=1
    ShowIconified=1
    ShowMapped=1
    ShowAllDesks=0
    UseMouseWheel=1
    UseUrgencyHint=1
    FlatButton=0
    MaxTaskWidth=150
    spacing=1
  }
}
Plugin {
  type=volumealsa
  Config {
  }
}
Plugin {
  type=tray
  Config {
  }
}
Plugin {
  type=indicator
  Config {
    applications=1
    datetime=0
    messages=0
    network=0
    session=0
    sound=0
  }
}
Plugin {
  type=dclock
  Config {
    [COLOR="#FF0000"]ClockFmt=%I:%M %p[/COLOR]
    TooltipFmt=%A %x
    BoldFont=0
    IconOnly=0
    CenterText=0
  }
}
Plugin {
  type=launchbar
  Config {
    Button {
      id=/usr/share/applications/lubuntu-logout.desktop
    }
  }
}
```


If needed you can reload the panel with... 
```
lxpanelctl restart
```

If you add the panel config to **/etc/skel/.config/lxpanel/Lubuntu/panels**,
any newly created accounts will include this config.

Hope this gives you enough info to do something with.

---

### Post by jdo300 on 2016-10-18
Thank you CantankRus! This solution works perfectly for me!

---

