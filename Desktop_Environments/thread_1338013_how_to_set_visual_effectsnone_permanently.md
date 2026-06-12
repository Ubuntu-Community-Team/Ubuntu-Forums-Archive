---
title: "how to set visual effects:none permanently?"
date: 2009-11-26
forum: Desktop Environments
---

### Post by stock99 on 2009-11-26
If only the visual effect doesn't upset the extended second screen, i wouldn't want to turn off the visual effect. But as a quick fix(so i can get to my work), I need to turn it off permanently (well, at least until the issue is fixed).  

Everytime I reboot the ubuntu9.10, the visual effects setting keep reset back to "normal" instead of staying at "none" and thus give me black screen after login. Is there a way to make ubuntu "remember" the setting of none across reboot?

---

### Post by yossell on 2009-11-26
Hmm - that shouldn't be happening. 

As I understand it, Ubuntu uses compiz for normal and extra effects, but uses metacity as a window manager for the option none. So you want to find the config file which tells Ubuntu what window manager to start up with and change it - it seems it's not saving the information when it quits. 

I'm on 9.04 so this may not be the same, and I may not be right anyway...but maybe try this:

go to  /home/~/.gconf/desktop/gnome/session/required_components

(~ will be the name of your own home folder)

and try opening the file %gconf.xml there in a text editor. 

Hopefully, you see something like this:
<?xml version="1.0"?>
<gconf>
    <entry name="windowmanager" mtime="1258797724" type="string">
        <stringvalue>compiz</stringvalue>
    </entry>
</gconf>

Replace 'compiz' with 'metacity', save, and try again. 

Even if things are differently arranged on 9.10, you may have to do a little experimenting to find the right files -

---

### Post by stock99 on 2009-11-26
I can find the file in the path you gave and the content seems always just "metacity" no matter which visual effects setup i am in.

```


<?xml version="1.0"?>
<gconf>
	<entry name="windowmanager" mtime="1259250004" type="string">
		<stringvalue>metacity</stringvalue>
	</entry>
</gconf>


```


*********
Just a side question, does 9.04 suffer the same fullscreen flash streaming video problem and dual extended screen issue? 
I have a feeling this setting visual effect mode is also buggy...

---

### Post by yossell on 2009-11-26
Hmm - I don't know what to suggest then.

I don't have a dual screen set up, so I can't answer that question, but I have read of a number of people having problems with such a set up. 

Is it possible to add a line to the start-up file so that it runs 'metacity --replace' after start up - not a great fix, I know, but it may have the effect of avoiding the black screen? 

If it's not a bug, I'm afraid I'm not sure why you're getting that effect.

---

### Post by miniyak on 2009-11-26
im having the same issue in 9.04, i have to set effects to none everytime i start up just to get games to work at there best

---

### Post by stock99 on 2009-11-27
hmm... I saw other thread about 'envyNG' package. I go install it and now i can't even get into console (ctrl+alt+F1/2/3/4/5/6)

All it does just blinking login prompt like 10 times a second. It is simply too fast for me to out type. I went into recovery mode and uninstall the navidia driver (btw, my laptop is Lenovo 3000 N100), but after reboot still same blinking login prompt.


Can someone suggest me a way to restore the default video driver?

---

### Post by JustinR on 2009-11-27
In my startup applications I found a Compiz entry that replaces Metacity with the compiz windows manager at startup - look for that in your startup application and remove it if it exists.

---

### Post by stock99 on 2009-11-30
err, but i can't even get back to GUI.
Is there a way i can do without reinstall entire OS?  My display driver got screw up because i attempt to install envyNG. Even after uninstall the nividia driver the OS still flashing a million time of command line login prompt at startup(usually just display for a few second and then display GUI login screen).

anyone can help? Or should i open another topic to solve that issue first?

---

