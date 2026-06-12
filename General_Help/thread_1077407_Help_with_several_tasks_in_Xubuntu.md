---
title: "Help with several tasks in Xubuntu"
date: 2009-02-22
forum: General Help
---

### Post by Compintuit on 2009-02-22
Hello all. I'm trying to do several things this morning, and am hoping you can help. I tried for several hours last night to remap some keys, using an Xmodmap file. I really don't want to use an app. My goal is threefold: 

My caps key to backspace
My shift key to Right Control
The audio key for previous to next.  

The file I have created is this:
remove Lock = Caps_Lock
keycode 66 = BackSpace Terminate_Server
keycode 118 = Shift_R NoSymbol
keycode 173 = XF86AudioNext NoSymbol
 I think it should work, but it doesn't.
I also am trying to autoload it with the code found here, [http://cweiske.de/howto/xmodmap/allinone.html](http://cweiske.de/howto/xmodmap/allinone.html)
by adding the line 
[ -f /etc/X11/Xmodmap ] && xmodmap /etc/X11/Xmodmap
to the script at /etc/X11/xinit/xinitrc

So where did I go wrong?

Next, I can no longer use horizontal scroll in Xubuntu - what do I need to do to enable it? it's not in any GUI, that's for sure. Next, While I still used windows, I could scroll to the end of the mousepad, and it would keep scrolling when I let go. I really have no Idea how to enable that in Xubuntu. Any Ideas? 

Next, for all my life I have used firefox with times new roman, no Antialiasing. I just can't give it up. But I do like antialiasing, and would like the rest of my computer to use it. So how would I go about selectively enabling apps not to use it?

Next, does the Fn key have any use in linux? My Fn key is not even seen by  xev. It worked nicely in windows for making non-english characters, as well as a row of predefined alternate functions for the f1-f12 keys.I'd like that back, if I could. 

I also want a way to open files from the filemanager as root - I keep having to go to terminal and open them as root there. Kinda annoying. 

And finally, I'd like some advice on what to do with basket note pad. I moved to Xubuntu because I wanted speed and space. Basket note pad installed Kmail, Kontact, Korganiser, and Kaddress book with it, unwanted.  TBH, that's something I would expect from a windows app. Basket note pad apparently depends on them, so if I kill them it goes too.  I don't really want another set of personal managers - I use Evolution, and am quite satisfied. how much speed and space am I losing to those unwanted extras? If it's a lot, I may kill basket note pad. But I do like it. There isin't any way to use it without those programs, is there? 

So that's pretty much what I hope to accomplish today - I hope you can help! 
Thanks in advance.

---

### Post by Compintuit on 2009-02-22
Does no one really have any help to offer?

---

### Post by Compintuit on 2009-02-23
:( Last try at a bump...

---

### Post by mb_webguy on 2009-02-23
Patience, my young padawan...  You've bumped your post twice in little over 12 hours.  This is an international forum, and the person(s) able to answer your question aren't necessarily awake or home from work yet.  It's generally encouraged that you don't bump a thread more often than once every 24 hours (though I personally think once every 12 for a critical issue is fine), but you certainly shouldn't give up on a thread until at least 24 hours have passed.

Unfortunately, I can't help you on this, but it's about time for our Kiwi and Aussie friends to be getting home from work.  Maybe you'll see some help shortly.

---

### Post by Compintuit on 2009-02-25
Hope I waited long enough for a bump :P

---

