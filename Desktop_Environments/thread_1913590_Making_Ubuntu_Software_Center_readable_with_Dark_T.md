---
title: "Making Ubuntu Software Center readable with Dark Themes"
date: 2012-01-22
forum: Desktop Environments
---

### Post by The_Third on 2012-01-22
I know a number of people have trouble using dark themes with Ubuntu because the software center likes to keep its white background and also use the default light colored text. The following solution is pretty hack-tastic and I'm hoping to hear some more elegant ideas.

1) Open up a terminal and type:
```
gksudo gedit /usr/share/software-center/ui/gtk3/css/softwarecenter.css
```

2) The first two lines should look like this:
```
@define-color light-aubergine #DED7DB;
@define-color super-light-aubergine #F4F1F3;
```

Copy and paste those two lines right below then comment out the originals. Change the two HTML color codes (#DED7DB and #F4F1F3) to your preferred dark colors so that light text will show up.

3) Save and close gedit. Launch Ubuntu Software Center to check out the results

---

### Post by Hreinsi on 2012-01-22
@define-color light-aubergine #DED7DB;
@define-color super-light-aubergine #B4A66F; works fine Thanks

---

### Post by vasa1 on 2012-01-22
> **The_Third said:**
> I know a number of people have trouble using dark themes with Ubuntu because the software center likes to keep its white background and also use the default light colored text. The following solution ...

```
gksudo gedit /usr/share/software-center/ui/gtk3/css/softwarecenter.css
```

2) The first two lines should look like this:
```
@define-color light-aubergine #DED7DB;
@define-color super-light-aubergine #F4F1F3;
```

...
Thank you for sharing! I had [asked about this]("http://ubuntuforums.org/showthread.php?p=11633002#post11633002") a while ago and couldn't find the solution myself.

---

### Post by The_Third on 2012-01-26
I'm glad i could help ^^
I'm sure you all noticed that during the recent Software Center upgrade the background color reverted back to white; there has to be a more permanent solution, right? I know a lot of themes have definitions for some specific apps like nautilus, but I'm not sure if there's a way to do that for software center.

---

### Post by vasa1 on 2012-01-27
> **The_Third said:**
> I'm glad i could help ^^
I'm sure you all noticed that during the recent Software Center upgrade the background color reverted back to white; there has to be a more permanent solution, right? I know a lot of themes have definitions for some specific apps like nautilus, but I'm not sure if there's a way to do that for software center.
Yes, it did revert but I fixed it again. Maybe the upgrade installed a new .css file with the "old" colors?

---

### Post by blas4me on 2012-08-25
I just wanted to say thanks a bunch, I love my dark themes, and all that white was killing me.

---

### Post by xraynetcontrol on 2013-03-21
thank you!!! i too have been searching for this. much appreciated!

---

### Post by Awesomefireduck on 2013-12-22
I made a screenshot and used gimp to find the gnome dark theme colours:
it looks great!
```
@define-color light-aubergine #393F3F;
@define-color super-light-aubergine #393F3F;
```
you can paste these below the original ones and comment the original colours out.

---

### Post by QNEPFmr on 2014-04-13
I have Gnome 14.04 installed but this problem still exits.. :(

---

### Post by vasa1 on 2014-04-13
> **QNEPFmr said:**
> I have Gnome 14.04 installed but this problem still exits.. :(
That's because the people who design the USC don't see it as a problem :)

Maybe you could file a bug or feature request?

---

### Post by averos on 2014-04-18
I don't have dark theme turned on but i am using Adwaita and selected items in software center were completely messed up and text was unreadable. 

I opened the CSS file as described by others above
```
 gksudo gedit /usr/share/software-center/ui/gtk3/css/softwarecenter.css

```

Then under the two @define-color lines added a third line so the first three lines now look like this

```

@define-color light-aubergine #DED7DB;
@define-color super-light-aubergine #F4F1F3;
@define-color selected_bg_color #4B97C4;

```

Now the highlighted background is pretty much the same shade as the Adwaita theme. :KS

---

### Post by narcisgarcia on 2014-08-21
Bug and workaround comments:
[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/899878](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/899878)

I prefer Tommy Miller's file (softwarecenter.css) but with:
@define-color super-light-aubergine #555555;

---

### Post by chicknhawk on 2014-08-22
Try this combination. Looks real nice.

/*
    @define-color light-aubergine #DED7DB;
    @define-color super-light-aubergine #F4F1F3;
*/

@define-color green #98FB98;
@define-color limegreen #32CD32;

[IMG][[IMG]http://i125.photobucket.com/albums/p65/h2ohboy/76fd1af2-c6c4-4451-93e5-162bdbce086c.png[/IMG]]("http://s125.photobucket.com/user/h2ohboy/media/76fd1af2-c6c4-4451-93e5-162bdbce086c.png.html")[/IMG]

---

### Post by chronictron on 2014-09-17
This problem had been urkin me for some time now, thanks big time for the quick fix!

---

### Post by andresroga93 on 2014-10-07
Such class... you, sir... are a genious!

---

