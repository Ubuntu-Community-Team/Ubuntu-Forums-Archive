---
title: "Replacement for itunes?"
date: 2006-03-24
forum: Desktop Environments
---

### Post by jenred on 2006-03-24
Hello!

Ubuntu is running well on my Inspiron 700M, can do pretty much everything and more then I could in WindowsXP, with one major exception. No itunes.

Multimedia management is very confusing.  How do I sync up my nano? How do I listen to podcasts?  How do I watch quicktime videos? What do I do with wmv files?I used to start the day listening to the Onion and now nothing.  So I tried downloading and installing various management tools -- but I wound up with around 6 different applications doing what itunes  used to do in one.  I just want to manage playlists, listen to and update podcasts (including being able to **watch** Ask a Ninja!, and occaisionally rip a few cd's -- preferably using one application.

Is there anything that can do the above and run under Ubuntu or Linux in general?  And no I don't want to have to run some windows emulator...

Suggestions greatly appreciated!  

Jen

---

### Post by petervk on 2006-03-24
You might have already tried this, but Amarok is probably the closest to itunes in terms of features. 

To install amarok open a terminal and type: 
```
sudo apt-get install amarok
```

To be able to play the restricted formats, try out [Automatix]("http://www.ubuntuforums.org/showthread.php?t=80295").
"Option 1) Installs multimedia codecs" should get all the required files installed with the exception of totem-xine.

To install totem-xine open a terminal and type:
```
sudo apt-get install totem-xine
```

That will install the slightly more capable totem-xine which after the multimedia codecs from Automatix are installed will be able to play *.mov files.

I think Amarok can rip cd's just the way it is. To burn cds from amarok install k3b. (sudo apt-get install k3b)

Crap, just found [this How-to]("http://www.ubuntuforums.org/showthread.php?t=103071"). Should answer all your questions.

---

### Post by aysiu on 2006-03-24
There is no replacement for iTunes.

Sure, some people will say that iTunes sucks, and it's slow and bloated and whatever.

That hasn't been my experience, and I don't think I'm alone. iTunes is slick, extremely functional, and easy to use.

I see no compelling reason to separate out iPod integration, CD-ripping, music organization, song purchasing, tag labeling, etc. apart from the abstract idea "bloat."

You will be able to find applications that, together, approximate the tasks iTunes performs, but you won't find one application that's an iTunes replacement.

I've grown to love AmaroK and Gtkpod and Goobox and EasyTag/TagTool.

If you can't grow to love some combination of Linux apps, consider buying Crossover Office--you can run iTunes through that.

---

### Post by phibxr on 2006-03-24
```
sudo apt-get install quodlibet
```

A fantastic player with a paned browser. Similar to Banshee and Rhythmbox, but in my opinion quite superior.

---

### Post by angkor on 2006-03-24
[QUOTE=aysiu]There is no replacement for iTunes.

Sure, some people will say that iTunes sucks, and it's slow and bloated and whatever.[/QUOTE]

That's probably because you used the Mac version of iTunes in stead of the windows one ;) 

My experience with iTunes on windows was (long time ago and no idea what iTunes is like nowadays) quite different.

@jenred: I like Amarok, and use it for music playing, managing my library and managing my iPod. Give it a go if you haven't already. It seems to do everything you ask for except playing quicktime movies.

---

### Post by aysiu on 2006-03-24
[QUOTE=angkor]That's probably because you used the Mac version of iTunes in stead of the windows one ;)[/quote] Actually, that may by why most people like iTunes (I don't know--I can't speak for most iTunes fans), but I used it on Windows, and it was fine. I know others have had issues with the Windows version, but I haven't.

Over time, though, I have to say I've grown to appreciate parts of JuK and AmaroK that I can't live without, and when I have to use iTunes at work, I'm sad that, for example, my global keyboard shortcuts are gone.

---

### Post by rfruth on 2006-03-24
I use iTunes on my older G3 iMac and a couple XP boxes and it works well !  On my Ubuntu machine I use Rapsody, its Linux friendly and there is a free trial with no strings attached ! [http://www.rhapsody.com/myrhapsody?pageid=rotw.homepage]("http://www.rhapsody.com/myrhapsody?pageid=rotw.homepage")

---

### Post by kennethb on 2006-03-24
You may want to look at 'gtkpod'. I don't use my computer for music much. I guess I'm a old CD and radio enthusiest. Someone told me about 'gtkpod' for using an iPod with a Linux box.

---

### Post by fxgogo on 2006-03-28
I don't understand why there has not been an itunes replacement already. Surely it can not be that hard to make? If I had the programming skilss I would surely try.

---

### Post by ThirdWorld on 2006-04-17
[QUOTE=fxgogo]I don't understand why there has not been an itunes replacement already. Surely it can not be that hard to make? If I had the programming skilss I would surely try.[/QUOTE]


thats because all these nerds fluent in klingon, love to compile all the linux crap by themselves and play their mp3 files in their consoles, it make them feel intelectually superior... so they dont understand why the rest of us, 95% of the end users, need an itunes replacement... ](*,)

---

### Post by Super King on 2006-04-17
There are numerous iTunes *replacements*, but no iTunes *clones*.

---

