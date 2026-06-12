---
title: "Using the CAPS LOCK key as a custom shortcut key"
date: 2016-05-25
forum: Desktop Environments
---

### Post by MykalAnderson on 2016-05-25
Hi all, Long time reader first time poster. (I think, maybe I have posted stuff, I should probably check that)

At work on a win machine I use AutoHotKey to create custom short-cuts. I have Autokey installed on my Ubuntu machine but I cant find a way to use the CAPS LOCK key the same way I do with AutoHotKey. I thought I would ask here if there were any know solutions to provide the required behaviour.


[LIST]
[*]CAPS LOCK operates normally when pressed and released with no intervening key.
[*]While CAPS LOCK is pressed, any other key pressed can run a CLI command, and then does not toggle CAPS LOCK.
[/LIST]

As examples


[LIST]
[*]I have a web page at work I use a lot. I hit CAPS LOCK + "P" and it runs **> path/iexplore.exe - page **without toggling CAPS
[*]If I want to open a page in Firefox instead of IE (default by necessity in my SOE) then I copy the URL and hit CAPS LOCK + "F" and it will run **> path/firefox.exe - "clipboard", **without toggling CAPS.
[*]I have the need to copy without formatting. I hit CAPS LOCK + "C" and it copies any text from the selection into the clipboard without formatting, without toggling CAPS
[/LIST]

Any tool exist to do this? It seems answers only provide methods to disable or reassign as another shift/control/super key or similar.

If not, this might be an interesting coding project and I'm willing to learn so any pointers for that would also be appreciated.

---

### Post by him610 on 2016-05-25
You can check out this link...
[http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys-or-devices]("http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys-or-devices")

---

### Post by MykalAnderson on 2016-05-26
Hi him610,

Yes I had seen this. It really doesn't give the behaviour needed though, it's just mapping it to another key. If I mapped it to super/alt/control/shift it would just be an additional one of those keys, and in most cases I already have 2.

The reason that I find using the CAPS key this way on my win machine at the office so handy is:
- caps is NEVER used in a combination with another key
- It NEVER does anything other than change the CAPS state
- it's always RIGHT THERE under my left pinkie

If I used any other key I would have to contend with ensuring that I don't interrupt any other normal behaviour. I used to use `, but I realised I actually use ~ alot for 'approximately' and in AutoHotKey the key just stopped working. CAPS in autohotkey works UNLESS another key is pressed while it is down. CAPS is just dying to be used this way.

I feel like I almost need a program to be running waiting for the CAPS lock key.

On CAPS keydown, wait for next

if other keydown/up, then run "this cli command" and exit (do not alter CAPS state)

If CAPS keyup, then alter CAPS state.

---

