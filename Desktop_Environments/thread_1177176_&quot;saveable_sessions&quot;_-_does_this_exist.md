---
title: "&quot;saveable sessions&quot; - does this exist?"
date: 2009-06-03
forum: Desktop Environments
---

### Post by tjoff on 2009-06-03
Hi

I have browsed around for a while without being able to find what I was looking for, maybe because it does not exist, maybe because I do not know which search terms to use.

The following use case is to illustrate the feature i am looking for:

I am working with a set of different applications, which i tend to use in the same way each time. For example when i program, i always have an emacs window and a terminal window in workspace 1, two terminal windows in workspace 2, a fullscreen paraview window in workspace 3, etc.
All these windows are positioned and resized as i like them.

My question is: Is there a feature in ubuntu to save this configuration and start such a session? And to select from a list of possible configurations?
(I know that you can resume your last session, but here I need to select from a list of "predefined sessions", e.g. "programming", "report writing", etc.)
I am currently using jaunty 64 bit on a dell laptop.

I also tried making a script to attain all this, start a set of applications and position their windows in the respective workspaces, but i have not succeeded in doing this. If someone has a script that is able to do this or something similar, I would be thankful for if you would care to share it with me.

---

### Post by tjoff on 2009-06-08
Due to the lack op response on this thread, I take it there is no commonly known way of doing this.
Meanwhile i discovered exactly this idea was already put up on brainstorm.ubuntu.com.
If you like the idea, you can vote for it on:
[http://brainstorm.ubuntu.com/idea/19104](http://brainstorm.ubuntu.com/idea/19104)
and/or propose modifications.

---

### Post by tjoff on 2009-06-08
btw,

From [http://www.sandklef.com/xnee/?q=node&q=introduction:](http://www.sandklef.com/xnee/?q=node&q=introduction:) 
"GNU Xnee is a suite of programs that can record, replay and distribute user actions under the X11 environment. Think of it as a robot that can imitate the job you just did." 

The above sounds as a possible solution for the above described problem.
Has anyone tried it, and does it work well?

It is in the repositories, and I tried installing and running it, but apparently there is currently a bug in its communication with Xorg ([http://www.sandklef.com/hesa/index.php/2009/05/28/record-extension-malfunctions-xnee-too/](http://www.sandklef.com/hesa/index.php/2009/05/28/record-extension-malfunctions-xnee-too/)), so it did not work this time...

---

### Post by tjoff on 2009-06-17
Hi

I am still on the search, and still hoping for some feedback in this forum.
The latest thing I found was that the command "gnome-session-save" saves the active session, and reloads it automatically next time gnome is started.
From what i can see from the man page, saving to and loading from a specific file is not possible.

But i imagine that what happens is that one or more config files must be saved somewhere. In that case, if one knew which these were, they could be copied and renamed. 
Then when one wants to start a new session, one overwrites the config file with one of the previously saved (containing the session one wants to continue), and restarts gnome. Thats it, support for multiple saveable sessions. Is it that simple? If so, a hint about which file(s) contain(s) the session would make my day :-)

As I said, I would very much like some feedback. Am I trying to reinvent the wheel? Am I not making clear enough what I am trying to do? 
Please give me your hints, I promise to make a nice HOWTO, whenever i figure it out :-)

Thanks for reading this far!

---

### Post by meranaamjoker on 2009-09-14
I am just searching searching searching for this feature. Its an amazing one.

Please share your experiences time to time on this thread. So far, I found nothing other than writing ones own perl scripts (for example) and launch all related applications with a single command.

---

### Post by tjoff on 2012-02-14
I finally stumbled upon a program that can do most of what I want to. 
The program 'wmctrl' is a command line tool to manage positioning and properties of application windows across workspaces.
I can now script a set of "profiles" of workspace configurations according to my needs, which is 90% of what I want.
I'll mark this as solved :-)

---

