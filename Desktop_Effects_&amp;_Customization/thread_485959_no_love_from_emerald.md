---
title: "no love from emerald"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by sublimation on 2007-06-27
I've got compiz to run fine with metacity, but what about emerald? should i be doing anything special to get it to run well? emerald --replace & only causes decorations to disappear, or nothing to happen at all, depending on the weather, position of the moon, which stars are rising to their zenith, and maybe a couple of settings, but I doubt it.

Can anyone help spread the love?

---

### Post by hyperair on 2007-06-27
Firstly,it's not compiz running fine with metacity. That's gtk-window-decorator you're talking about, or Heliodor. Gtk-window-decorator doesn't follow the Metacity theme, whereas Heliodor does, I think. I'm not too sure about that though, because I've been with Emerald from the days of CGWD all the way on.

Secondly, Emerald was made to work with Beryl. If you are running Ubuntu Gutsy, then the Emerald packages don't work. That's because the Emerald packages in Gutsy's repository are 0.2.1, whereas Compiz Fusion packages are at 0.3.* or something of that sort. You need to upgrade Emerald to 0.3.* to get it to work, which unfortunately I don't know how to, as I don't run Gutsy.

As for working in Ubuntu Feisty. If you're using Compiz Fusion, then you can use Emerald. Otherwise, no. Before Compiz Fusion, Emerald was a Beryl-only window decorator, due to some differences in the Beryl core, or so I heard. If you want Compiz and Emerald, then go install Compiz Fusion. There's a nifty tutorial over here: [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

If you're in Ubuntu Edgy or Dapper, I'm sorry I can't help you, as I've been with Feisty since its release, and haven't kept in touch with any Edgy or Dapper news.

---

### Post by sublimation on 2007-06-27
excuse my previous confusion (forgive the pun). I think I understand what's happening a little better. I currently have compiz fusion running on feisty. It starts without any window decorator. Using compiz --replace will have no effect at this point. I usually then go for metacity --replace, then compiz --replace and all works as though compiz should. 
with a little bit of package reinstallation now emerald --replace brings up whichever theme i've selected for emerald, hoorah!

just a quick question left, how do I make it so that the windows do not start out frame-less?

---

### Post by hyperair on 2007-06-28
Aha so you got Emerald working! Now here's the code:
```
compiz --replace -c emerald
```

If you want to make it load with Compiz and Emerald on start up, you could add that to System->Preferences->Sessions

---

### Post by sublimation on 2007-06-28
wonderful!
it all seems so simple now, but alas, it was a headache at the time. I guess that's what happens when you fall into the learning curve with your feet moving. 
Thanks for the help!

---

### Post by hyperair on 2007-06-28
Caution: The most recent Compiz Fusion update has seemingly disabled that command. It starts gtk-window-decorator instead of Emerald, completely ignoring the "-c emerald" flag behind it. In this case, you should start Compiz with two commands instead of one:
```

#!/bin/sh
compiz --replace
emerald --replace

```

I'd suggest putting it into a text file, and making it executable, and then putting the path of the textfile into the startup programs.

---

