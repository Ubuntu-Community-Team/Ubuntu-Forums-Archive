---
title: "Closing xterm closes firefox"
date: 2007-02-12
forum: Desktop Environments
---

### Post by backdoor on 2007-02-12
Hello,

I am wondering if anyone is seeing the following issue that I am in a Kubuntu system.

I usually open Firefox etc. from an xterm window so I can see if there are any failures/errors etc.
I recently installed Fiesty Fawn and was noticing that after I've opened Firefox from an xterm, if I now close this xterm, Firefox automatically goes away as well.  Now, I understand if I hadn't opened Firefox with the '&' at the end, but I do put it.

So, I tried a few more things:
1) Opened Konqueror from xterm and closed the xterm.  Konqueror goes away.
2) Opened Firefox from konsole and closed konsole.  Firefox goes away.
3) Opened another xterm from an xterm and closed the original one.  The second xterm does *not* close in this case.

I figured this might be a Fiesty Fawn bug or something, but just wanted to be sure, so I loaded up Edgy Eft.  Exactly the same thing as mentioned above happened here.

I don't see the same problem in Dapper Drake.

If I open a child process from a parent process while using the ampersand, I don't believe the child process should die when the parent process is closed.  Any ideas what's going on?  

Thanks for any insight in advance.

---

### Post by paparucino on 2007-02-12
> **backdoor said:**
> 
If I open a child process from a parent process while using the ampersand, I don't believe the child process should die when the parent process is closed.  Any ideas what's going on?  

It works as expected for me. I tried some combinations (always with ampersand) and firefox is always up.

---

### Post by daou on 2007-02-12
Could there be a setting in xterm that kills all child processes once xterm itself quits?

---

### Post by paparucino on 2007-02-12
> **daou said:**
> Could there be a setting in xterm that kills all child processes once xterm itself quits?
According to man xterm, there is nothing.

---

### Post by backdoor on 2007-02-12
Hi,

Thanks to all that replied.  I am still not sure what's going on, but seems like it must be something I did that is causing this :), although, I am not sure what.

As I had said before, this isn't happening for all applications.  Well, it seems like it is not happening only if I open another xterm from the original xterm.  Otherwise, so far, all the applications I tried are closing down (firefox, konqueror, xemacs, kate).

So, to debug this further, I used the following command: strace -o konq_trace.txt konqueror&

When I close the xterm, the strace shows that konqueror received a SIGHUP and thus closed down.

Still trying to figure out why a SIGHUP is getting sent to it.

Thanks

---

### Post by Medieval_Creations on 2007-02-12
I've done that before to.  I couldn't explain why xterm was setup like that but as far as I've been aware it's always done that.
Here's something to try; when you launch and application in xterm at the end of the command put a &.

Example:
```
firefox &
```
```
konqueror &
```

The & tells linux to run the program in the background.  Then when you close xterm what ever app you opened should remain until you close it.

I launch apps like this all the time because I almost always have a terminal up and by launching a program without the & the terminal is locked into running that app.

---

### Post by backdoor on 2007-02-12
Hi Medieval_Creations,

I always use the & after the application name to start the application.  But, that is what's baffling.  Why, even after using the &, the application closes when the xterm it was started on is closed.

After a little more experimentation, there are a few more things I have learned:

1) This is a bash thing.  I created 2 brand-new users.  One with bash shell and the other with csh.  From both users, without any changes, if I open an xterm and an app from within this xterm and then close the xterm, the app closes on the bash user, but not on the csh user.

2) The app closes if I hit the "X" on the top right hand corner of the xterm to close the xterm.

3) The app does *not* close if I specifically type 'exit' on the xterm.

4) I have a Debian Etch machine too that I opened an app from an xterm and close that xterm.  The app closes the same way.  The user on this Debian machine is also using bash.

---

### Post by daou on 2007-02-13
Maybe it could be an environment value. For example, when you load bash, it loads its config and env. values from files (~/.bashrc is one of them). Maybe one of these values controls whether the SIGHUP is sent when xterm closes. I'm afraid I cannot give better advice than this.

---

