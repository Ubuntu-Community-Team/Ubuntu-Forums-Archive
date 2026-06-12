---
title: "Shell/terminal -&gt; shortcut for opening a directory path?"
date: 2012-03-22
forum: Desktop Environments
---

### Post by janisgeiger on 2012-03-22
Hey!

I've been looking for a shortcut that would let me open a directory I specify in the terminal in the default file-browser, perferably cross-plattform, linux-general-wise. Now, there's pcmanfm /usr/share, or nautilus /usr/share, but that's longer to type than going there by mouse.

The best option so far is: gnome-open, when being in a gnome desktop environment, which would open either the default file browser or the default web browser if I typed in an URL.

But isn't there anything shorter than this :confused: I'm baffled that linux people obviously really don't like the combination of a file browser and the terminal if such a short command has never been invented! (comparison on a mac: "open")

Anyway, maybe an aditional keybind to the gnome-terminal might help (?) but I've never really tried looking for it not soo sure if that's possible at all. +that's also not very direct.

Cheers! Gonna invent that command now and get rich:lolflag: (karma-wise.)

---

### Post by papibe on 2012-03-22
Please ignore my post. Completely different concern.

> Hi janisgeiger.

There's a nautilus extension that allows you to right click on it  and open a terminal on the current path.

To install it:
```
sudo apt-get install nautilus-open-terminal
```
Check more nautilus  extensions [here]("http://www.techdrivein.com/2010/09/6-useful-nautilus-extensions-and.html?m=1").

Hope it helps.
Regards.

---

### Post by janisgeiger on 2012-03-22
ah, ps. thought about it. maybe just starting a default "browse" terminal would help, so that gnome-open would be accessible via up cursor.


So, to improve this thread, here's another thing I'm still uncertain of:
If I extract a tar.gz and compile / install the software/the package via ./configure make and (sudo) make install, 

can the folder be deleted afterwards? and what exactly does "make clean" do?
if the folder may not be deleted, I assume it's best to extract archives always in a good structured default directory like usr/src or usr/share, right?
what's the most common one established in linux?

cheers.

---

### Post by janisgeiger on 2012-03-22
thanks ;) very unsure if that's what I was looking for though.
it's an extension, not a terminal command, also works only with nautilus + it doesnt open a file browser via the terminal, but a terminal via the file browser ;) (if I understood correctly) nevermind! not thaaat important. cheers.

---

### Post by markbl on 2012-03-22
I've always used "xdg-open" for what you are talking about. E.g. I am sitting in a directory within a terminal window and I decide I want to open Nautilus (GUI) on that directory. Then I just type
```

xdg-open .

```

This works in kde, gnome, and others.

To your other question about installing software from configure source (you should have created a new thread btw!), yes you can just delete the entire directory. The make install copies everything to the installation dir (usually /usr/local). Note however that you can usually do a "make uninstall" from that source dir which will remove everything it installed in /usr/local. So if you delete your source dir then you lose the ability to (easily) remove the new software.

---

### Post by LewisTM on 2012-03-22
If you want a shorter command (e.g. 'go'), there is nothing preventing you from either making an alias in your .bashrc
```
alias go="xdg-open"
```
Or making a symlink (my favorite, not limited to bash shells)
```
sudo ln -s /usr/bin/xdg-open /usr/bin/go
```
Then just call 'go' for anything and everything
```
go .
go myfile.pdf
go http://website.com
```

Cheers!

---

### Post by asmoore82 on 2012-03-22
> **janisgeiger said:**
> can the folder be deleted afterwards?
Yes, but someday you may need it to `sudo make uninstall` 

> **janisgeiger said:**
> and what exactly does "make clean" do?
I think it deletes everything that previous `make`s did. So it returns the source tree to a clean `./configure`ed state.

> **janisgeiger said:**
> I assume it's best to extract archives always in a good structured default directory like usr/src or usr/share, right?
Extracting, configuring, and compiling source doesn't require root privilege and it's always best to keep root to a minimum. Out of ancient habit, I always use "$HOME/src"
But if I were concerned with cosmetics or if setting up a machine for a friend, I would probably use "$HOME/.local/src"

---

