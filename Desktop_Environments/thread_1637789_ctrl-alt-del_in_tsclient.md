---
title: "ctrl-alt-del in tsclient?"
date: 2010-12-04
forum: Desktop Environments
---

### Post by Jeff Morris on 2010-12-04
I'm using tsclinet to connect to Windows (ick, I know) servers.  I can't get tsclient to pass through ctrl-alt-delete to the remote server, which of course is needed under Windows to login.

I know that tsclient is just a front-end for rdesktop, and what's interesting is that if I start rdesktop directly from the command line, ctrl-alt-delete works as expected.  It's almost as if tsclient is launching rdesktop with a different keyboard map or some such.  I'd really prefer to use tsclient for the ease of use factor though, rather than set up a bunch of shortcuts to servers via rdesktop.

The only thing I can find in tsclient's dialogs related to the keyboard is a country setting, which I have set to "us".

I've not been able to find much in the way of documentation for tsclient.  The man page is very sparse, as is the developer's web site.

- Jeff

---

### Post by conradin on 2010-12-04
try rdesktop from the terminal. 
Thats what I do.
```

rdesktop -u <username> <IP>


```

---

### Post by Jeff Morris on 2010-12-04
Right... well, as I said in my OP...

"what's interesting is that if I start rdesktop directly from the command  line, ctrl-alt-delete works as expected." ... "I'd  really prefer to use tsclient for the ease of use factor though, rather  than set up a bunch of shortcuts to servers via rdesktop."

So I already said that I know I could do it that way, but as part of my job I frequently have to log in to  many different Windows servers, and I'd like to be able to set other options in tsclient, and not have to pass them all as command line switches, or create a whole bunch of different rdesktop config files.  That's the whole point of tsclient, to provide a convenient run-time interface to rdesktop so that one doesn't need to do all of that, and I want to use it for  it's intended purpose.  I'm just trying to figure out why when rdesktop is launched from tsclient, ctrl-alt-delete stops working, that's all. :-)

Thanks.

- Jeff

---

### Post by conradin on 2010-12-05
you could try running tsclient from the terminal to see if you get any stderr while trying to use your commands.

also, what do you have set in the performance tab?

---

### Post by Toz on 2010-12-05
I've found that if I start a client session with tsclient, for some reason, the tsclient window doesn't have focus (even if its full screen and/or looks like it has focus). I first have to click in the window (I click on the login dialog), then Ctrl-Alt-Del works for me. YMMV.

---

### Post by Jeff Morris on 2010-12-08
> **Toz said:**
> I've found that if I start a client session with tsclient, for some reason, the tsclient window doesn't have focus (even if its full screen and/or looks like it has focus). I first have to click in the window (I click on the login dialog), then Ctrl-Alt-Del works for me. YMMV.

I've been away from work the last three days, so I haven't been able to test this on the computer I was having the problem on.  I did test it on my own Ubuntu 10.10 laptop tonight though, and you're absolutely right... even if the window has focus, I found that I must move the mouse over it in order for ctrl-alt-del to be passed through.  It's almost as if I have my window manager set to auto focus under the mouse, but I know I do not.

Perhaps this is the problem with the system at work too.  I will post here after I'm able to try it tomorrow.

Thanks.

---

### Post by Jeff Morris on 2010-12-08
> **Jeff Morris said:**
> Perhaps this is the problem with the system at work too.  I will post here after I'm able to try it tomorrow.

Well, I'm back at work today and... no dice.  Behavior on this machine is different from the one at home, even though they're both running 10.10, and to the best of my knowledge I haven't made any configuration changes that should effect ctrl-alt-del in tsclient.

Interestingly, when the rdesktop window has focus, ctrl-alt-del does nothing.  (If it doesn't have focus, then the Ubuntu shut down dialog pops up), so it appears that it is trapping the ctrl-alt-del key sequence, just not passing it through to the remote host as it should.

[QUOTE=conradin]you could try running tsclient from the terminal to see if you get any stderr while trying to use your commands.[/QUOTE]

I tried that today, and this may indeed be relevant, I'm getting:

ERROR: Failed to open keymap us

Not sure what to do about it though.

> also, what do you have set in the performance tab?Under the performance tab, I do not have any checkboxes selected.

---

### Post by Jeff Morris on 2010-12-08
> **Jeff Morris said:**
> I tried that today, and this may indeed be relevant, I'm getting:

ERROR: Failed to open keymap us

Well, that was it.  I simply set it to blank (no keymap) and now it works.

Thanks everyone.

---

