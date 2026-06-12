---
title: "Restrict session when user logs in"
date: 2010-04-11
forum: Desktop Environments
---

### Post by kenrmcl on 2010-04-11
G'day there One & All,

     My apologies if this question has been asked here previously, but if it has I can't find it or the solution.

     I have Xubuntu 8.04 working as a server on my Dell desktop at home. It's also occasionally used as a desktop machine, with GDM to log in. (nothing unusual so far).

     My special needs grandson logs in directly and uses it to play games. He only knows how to use Windows XP and so I run this in VirtualBox for him. What I'm trying to do is to simplify it so that he can just enter his username & password and it will automatically run the VirtualBox session.

     I know I can just run VirtualBox with XP after he's logged in, but that will run it as a program in a normal Xfce session. It won't be the specific session that I have set up (following instructions from elsewhere) that reduces resource requirements by not having the full host environment running in the background, although Xfce is pretty efficient anyway.

    The other option is for the VirtualBox session to be the default & I will select Xfce when I use it, but that's not as desirable as having it autoselect the session based on username although it may be the only option.

Thanks for listening and I hope you can understand my explanation of what I'm trying to do.

---

### Post by dominiquec on 2010-04-11
How about writing a simple shell script to invoke and run VirtualBox in the environment you want?  Then have the script autorun when your grandson logs in.

---

### Post by kenrmcl on 2010-04-11
> **dominiquec said:**
> How about writing a simple shell script to invoke and run VirtualBox in the environment you want?  Then have the script autorun when your grandson logs in.

Yep, that's certainly an option. I mentioned it in the 4th paragraph. There's a real good chance that this will be the way I end up doing it, but it's not really the same thing as once he logs in, the Xfce session will start and anything else runs in that environment. I'll end up with a full Xfce session running VirtualBox, then with XP inside that. It's not necessarily a bad thing as Xfce doesn't chew up a lot of resources, but running the VirtualBox session reduces the overhead right from the login (or so the VirtualBox forum told me).

Thanks for replying,
Ken

---

