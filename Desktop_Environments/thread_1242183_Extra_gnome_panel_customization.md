---
title: "Extra gnome panel customization?"
date: 2009-08-16
forum: Desktop Environments
---

### Post by wintersun on 2009-08-16
Hi everyone!

Could anyone tell me would it be possible to achieve this kind of a panel setup in ubuntu, like in this screenshot-2.png mockup? Screenshot.png is the default behaviour.

I need this cos the nature of my work demands A LOT of opened windows, so I need at least 2 rows in the panel, preferably 3. And by resizing it, all other items become bigger and bigger, so it takes up space for no reason. and honestly, it doesn't look so nice. So preferably it would be nice if it were also possible to make this single opened window (actually, button) not stretch up, like it does in screenshot.png.

Any ideas?

---

### Post by hictio on 2009-08-16
That's weird, it is not happening on my Ubuntu setup, running default Jaunty Gnome, with all the updates installed.

[URL=http://img33.imageshack.us/img33/4028/hugelowerpanel.png]
[IMG]http://img33.imageshack.us/img33/4028/hugelowerpanel.th.png[/IMG]
[/URL]

---

### Post by wintersun on 2009-08-16
> **hictio said:**
> That's weird, it is not happening on my Ubuntu setup, running default Jaunty Gnome, with all the updates installed.

[URL="http://img33.imageshack.us/img33/4028/hugelowerpanel.png"]
[IMG]http://img33.imageshack.us/img33/4028/hugelowerpanel.th.png[/IMG]
[/URL]

I think you didn't get me :)

I'm asking if its in any way possible to prevent those panel items from resizing together with the panel when I resize the.. well, panel. 

Screenshot-2.png is just a mockup I designed in Gimp, to show you the setup and behavior I'm trying to achieve.

---

### Post by hictio on 2009-08-16
Ooops, didn't quite get it... :(
Sorry.

---

### Post by wintersun on 2009-08-16
> **hictio said:**
> Ooops, didn't quite get it... :(
Sorry.

Haha, no problem bro. Do you happen to know any alternative to the Gnome panel that might work like this? I doubt this can be achieved anyway.

---

### Post by hictio on 2009-08-16
> **wintersun said:**
> Haha, no problem bro. Do you happen to know any alternative to the Gnome panel that might work like this? I doubt this can be achieved anyway.

No, not really, I was taking a look with gconf-editor to:

/apps/panel/default_setup/applets/window_list/
/apps/panel/global/
/apps/panel/general/

But I don't see anything regarding this... Perhaps on an accessibility option somewhere?

---

### Post by ccnjim on 2009-08-17
Is this what you mean? When I have a few windows open they're big. As I add more they double up. If I keep adding them 20 or more the titles abbreviate. Picture below. I should have read your post better. I'm sorry.

---

### Post by wintersun on 2009-08-17
> **ccnjim said:**
> Is this what you mean? When I have a few windows open they're big. As I add more they double up. If I keep adding them 20 or more the titles abbreviate. Picture below. I should have read your post better. I'm sorry.

haha, no prob.  People tend to misread this post for some reason :)

Nice theme btw

---

### Post by ccnjim on 2009-08-17
If it could be done it would be here right? I ask because the config. editor is where I go to play/break stuff.

---

### Post by TheNosh on 2009-08-17
you could just put all the stuff you don't want resized up on the top panel, leaving the bottom panel devoted to the window list. that's probably not what you would prefer, but it may be your best option. you don't seem to have much on the bottom panel anyway.

---

### Post by wintersun on 2009-08-17
> **ccnjim said:**
> If it could be done it would be here right? I ask because the config. editor is where I go to play/break stuff.

hmmm, yeah! seems like we might see some extras in later versions.

---

### Post by wintersun on 2009-08-17
> **TheNosh said:**
> you could just put all the stuff you don't want resized up on the top panel, leaving the bottom panel devoted to the window list. that's probably not what you would prefer, but it may be your best option. you don't seem to have much on the bottom panel anyway.

well, not right now :) I just reinstalled. :P

But that's not a bad idea!

---

### Post by theZoid on 2009-08-17
> **TheNosh said:**
> you could just put all the stuff you don't want resized up on the top panel, leaving the bottom panel devoted to the window list. that's probably not what you would prefer, but it may be your best option. you don't seem to have much on the bottom panel anyway.

Thanks what I would do, or what about a window manager plugin in the panel?  The one where you click it and lists open windows?

---

