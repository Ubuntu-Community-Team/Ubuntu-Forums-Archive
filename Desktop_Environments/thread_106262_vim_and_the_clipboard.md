---
title: "vim and the clipboard"
date: 2005-12-20
forum: Desktop Environments
---

### Post by bakert on 2005-12-20
I'd like to be able to copy/paste to the system clipboard when in vim in a terminal window.

I think you can normall do this using "* before cut/copy/paste commands but only if :version gives you +xterm_clipboard in vim.  Unfortunately the version that comes with Ubuntu 5.10 give -xterm_clipboard.

My questions are: (1) am I right in my conclusion? and (2) how do I get a +xterm_clipboard version on my machine.  Is there an apt-get type thing I can do or is it more complicated than that?

Thanks very much for your help,

Tom

---

### Post by Koybe on 2005-12-20
I'm not sure about what you wrote but you can use select and middle click for copy/pasting anywhere. You can even do that in a text console outside of X. maybe you'll need the gpm package then.. i don't know if it's installed in the base installation.

---

### Post by xtacocorex on 2005-12-20
I use vi in yakuake (a Quake-like Terminal Emulator) in KDE quite frequently and came across the problem of pasting external data, but one day I decided to use the default KDE konsole paste (shift + insert) and it worked. I don't know if it's different in Gnome, but it could be a start. 

As for copying from vi to the system clipboard, I don't know.

Hope this helps some.

---

### Post by bakert on 2005-12-20
Ctrl-Shift-V (the gnome-terminal equivalent of Shift-Insert) does indeed do exactly what you'd hope it would.

But I can't find a way to copy stuff to the clipboard from vim.  I think it must be to down to that :version information stuff.

Anyone know how I configure this most easily?

Thanks, Tom

---

### Post by bakert on 2005-12-21
Actually, Ctrl-Shift-V leaves me with serious indentation problems :( - each line is indented one shiftwidth further than the next.  I'm not sure why, don't want to have to :set noautoindent before pasting every time.

---

### Post by bakert on 2006-04-02
To copy to the system clipboard in vim use the '+' register.

So do something like:
V
<select text you want to copy now you are in visual mode>
"+
y

I think you need gvim installed for this to work, for some reason.

---

### Post by xenmax on 2006-04-02
For me this works: Text selection by mouse in terminal does copy ; middle mouse click does paste ; [ btw, if you dont have middle mouse button, clicking both left and right buttons does same operation]

PS: i was always under the impression that middle middle click and "Shift Insert" were 2 ways to same thing -  today i realised it not to be so :)

---

### Post by hagabaka on 2008-06-12
On Ubuntu Hardy vim.gtk provides xterm_clipboard, and it can run in terminal too. vim.basic does not. You can use update-alternatives to set vim.gtk as the default vim.

---

