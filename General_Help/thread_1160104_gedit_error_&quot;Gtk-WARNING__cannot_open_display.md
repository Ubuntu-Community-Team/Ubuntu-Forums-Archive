---
title: "gedit error &quot;Gtk-WARNING ***: cannot open display:"
date: 2009-05-15
forum: General Help
---

### Post by Muki on 2009-05-15
Hello! Was playing with gedit in a terminal session. Went to Ctrl-Alt-F1 and logged in as me (not su). Typed gedit test.txt and somehow there was an ' added after the .txt through a slip of the finger. Now test.txt was an empty file I had created with "touch". What I saw was a single > prompt (was it a >??) and whatever I tried, I couldn't exit gedit gracefully. Finally I wrote gedit again and was taken from the terminal session back into the GUI. Now, whenever I try to run gedit in a terminal session, I get the (gedit: xxxx): Gtk-WARNING **: cannot open display: error, where the xxx = different numbers each time.

Have googled the error message and it would seem this is different. I was not logged in as root at the time. ~$ is the prompt.

Any ideas?

---

### Post by Dr_Willis on 2009-05-15
>> Went to Ctrl-Alt-F1
>> Typed gedit test.txt and somehow there was an ' added after the .txt 

 This is the 'console' not X. you must use text based editors for the console such as vi, emacs, nano, or mcedit

>> What I saw was a single > prompt (was it a >??) and whatever I tried, >>>c ouldn't exit gedit gracefully.

Your extra 'quote mark' made the system wait for you to actually end the quoted statement. the > was the 'secondary' prompt telling you to finish your command.

if you had put in another ' it would of returned.


>>>  Gtk-WARNING **: cannot open display: error, 
See first comment. :) console is not X. 


>> Any ideas? 

spend some time reading a few bash tutorials and guides. Its worth the trouble.

The advanced bash scripting guide is a must read/bookmark, and theres literally dozens of other web sites with bash tutorials.
):P

---

### Post by Muki on 2009-05-15
Thank you, Dr Willis. I guess I assumed that there was a text-based as well as graphical version of gedit. I now know otherwise.

So, as long as I avoid gedit on the command line in console, everything else should work OK there??? I only get the error message when I try to use gedit there...

Thanks, Doc!

---

### Post by Dr_Willis on 2009-05-15
For any console work. You will normally need to use 'text/console' tools. 
there are alternatives for most of the X applicaions you may be wanting to use.

For a file manager, install and try out 'mc' the "Midnight commander"
it makes a lot of console work a lot easier. It will include the mcedit editor that is very handy.  Of course it pays to learn VI and learn it well.


```
sudo apt-get install mc
```

There are even text based web browsers, such as links, lynx and w3m.
Theres text based music and media players (you can even watch videos with mplayer and the proper asci-art libs/options.)


In short. About anything you do in X , you can find ways to do in the console.

I wont even get started on the coolness you can do with the 'framebuffer' enabled console.  :)

---

### Post by Knatchwa on 2009-05-27
That is certainly a work around but rather find a solution, as even with that you are not able to even run Synaptic as root. So though MC will work for somethings running synaptic does not work at all except to save marked changes in a download file. 

Looking forward to further suggestions on this challenge thanks.

---

