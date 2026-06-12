---
title: "Openbox pipe menu bigginers guide?"
date: 2013-02-27
forum: Desktop Environments
---

### Post by kabukiM0n0 on 2013-02-27
Hello

I'm in search of a  step by step guide about Openbox's Pipe menus? 
I find tons of information about everything else, but when it comes to how you have to create specific menus it's all extremely basic - add this here - that there and if you get such and such error something is wrong in the stated line within python. 

I'm pretty new to this level of file editing and playing around, obmenu is more or less under my command (maybe?). But when having to enter something into a python script I need something which tells me specifically what to do - if not, I just don't know what I'm doing. 


Is there anything like this out there? 

Thank you!

---

### Post by slickymaster on 2013-02-27
[Openbox: Pipemenus]("http://openbox.org/wiki/Openbox:Pipemenus")

---

### Post by kabukiM0n0 on 2013-02-27
EDIT:

Okay, this is where I start getting confused. 
I added this at the top of my menu, restarted openbox
```

<item label="pipe-weather">
            <action name="Execute"
                <command>
                    "python ~/.opt/gweather.py"
``` I'm getting X XML syntax error on line 688, with message: premature end of data in tag openbox_menu line 2.

---

### Post by slickymaster on 2013-02-27
> **kabukiM0n0 said:**
> I mean explain where this goes any why ```
</menu id="pipe-weather" label="Google Weather" execute="python ~/opt/gweather.py SPXX0016 Centigrade" "/> 
```


Personally, I never tried Openbox so I'm not really qualified to give you a correct answer.

But I did found you [this]("http://pclosmag.com/html/Issues/201110/page01.html"). It may help you, somehow.

---

### Post by kabukiM0n0 on 2013-02-27
That's where I started, with that article and things just started getting really complicated. But I think I may be onto something, maybe?

---

