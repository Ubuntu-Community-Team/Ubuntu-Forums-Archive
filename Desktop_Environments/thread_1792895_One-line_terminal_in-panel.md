---
title: "One-line terminal in-panel?"
date: 2011-06-28
forum: Desktop Environments
---

### Post by Candlehawk on 2011-06-28
I know what I am asking for is a touch specific, and if it doesn't exist, then I will probably try to write it myself, but this seems like the type of thing that must exist. I am looking for an application which has a small input field where I would input a single command and it would run the command in the terminal. I know that you can use the "Run application" application, but that opens up in a new field, and I just don't like that.

---

### Post by FormatSeize on 2011-06-28
> **Candlehawk said:**
> I know what I am asking for is a touch specific, and if it doesn't exist, then I will probably try to write it myself, but this seems like the type of thing that must exist.
Now that I think about it, this would be incredibly awesome. I don't know of anything like it that exists, though. But, you can emulate it with a program called tilda if you don't mind the fact that it's not set inside the actual panel. 
 
Grab tilda from the Software Center. What it is is a transparent terminal with no borders. You can resize it and set the background like you want it, then drag it so that it is positioned over your panel. If I recall correctly, it should open in that same place when you open it after closing it, but don't quote me on that.

---

### Post by ABCC on 2011-07-17
You could try bashrun:

[http://bashrun.sourceforge.net/]("http://bashrun.sourceforge.net/")
[IMG]http://bashrun.sourceforge.net/screenshot.jpg[/IMG]

Use gdevilspie to make a rule that undecorates bashrun, options such as center, above and focus are also quite good to set. With xdotool installed it can be made to run in the background. Finally, use ccsm to bind the command 'bashrun --show' to Win+R/your favourite shortcut. 

```

cd Downloads/
tar -zxf bashrun-0.16.1.tar.gz
sudo sh bashrun-0.16.1/install.sh
sudo aptitude install gdevilspie devilspie xdotool compizconfig-settings-manager

```

---

