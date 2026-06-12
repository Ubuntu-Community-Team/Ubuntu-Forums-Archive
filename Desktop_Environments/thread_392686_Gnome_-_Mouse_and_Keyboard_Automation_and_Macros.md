---
title: "Gnome - Mouse and Keyboard Automation and Macros?"
date: 2007-03-24
forum: Desktop Environments
---

### Post by mavicus on 2007-03-24
I can't seem to find anything on the net or the forum about software for Gnome that allows you to record or write a script of keyboard and mouse actions, then play it back for automation.

I heard of something called xnee and gnee, but when I install it from synaptic, I can't seem to get it to work, plus I'd like something that isn't so command line-ish if possible.

I'd also like the ability to launch these scripts from hotkeys, or either have the scripts listen for input and fire events based on the keys I press.

Something like "AutoIT" or "AutoHotKey" or "Perfect Keyboard" for windows.

Is there anything like this for Gnome?

Thanks.

---

### Post by ArieT on 2007-03-25
I was looking for a program like this for a long time and i couldn't find one until now. Tnx. 

But ...

I tried to install xnee with synaptic but i discovered this version is much to old. I downloaded the newest version from [this ftp](ftp://ftp.gnu.org/gnu/xnee/Xnee-2.05.tar.gz) and executed the following commands:
```

tar xvzf Xnee-2.05.tar.gz

```
```

cd Xnee-2.05

```
```

./configure
make
sudo make install

```
Now edit the file /etc/X11/xorg.conf and find the section "Module" and at the following line:
```

    Load  "record"

```
Restart X with ctrl+alt+backspace and start gnee, the gui version of xnee. Go to "Record Settings". Enable "Record from display" and fill in ":0.0" (without the quotes). Now set the 'recordables'. Don't press record yet because you haven't set a key for stopping the recordings.
Go to "Key bindings" and set some keys.

Now it should be possible to record your events. My computer crashes all the time running this program but perhaps you've got more luck.

I hope this helps a bit. If not ask.

(sorry for my English, I'm from the Netherlands and not used to write in English)

---

