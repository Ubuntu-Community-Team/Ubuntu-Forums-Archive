---
title: "Start multiple programs from bash shell?"
date: 2009-05-29
forum: General Help
---

### Post by EvanKroske on 2009-05-29
Hi, I'm trying to stop using my mouse, so I've started using the terminal to start programs instead of using the Applications menu. However, I can only have one programming running at once. All the programs I start from the terminal will only run as long as the terminal window is open, and I can't use the terminal while they're open. Is there an easy to start a program through bash so that the program isn't inferior to bash? Thanks.

---

### Post by Vunutus on 2009-05-29
The GNU screen utility might be of great use to you. It's most basic function is to act as something like tabbed browsing for terminals. It does other cool things like allowing you to detach a process from it's current terminal and re-attach it elsewhere (like another computer via SSH).

[This]("http://www.kuro5hin.org/story/2004/3/9/16838/14935") guide is the best screen guide I've found and it's what I used to figure screen out.

---

### Post by maheshasolkar on 2009-05-29
> **EvanKroske said:**
> Hi, I'm trying to stop using my mouse, so I've started using the terminal to start programs instead of using the Applications menu. However, I can only have one programming running at once. All the programs I start from the terminal will only run as long as the terminal window is open, and I can't use the terminal while they're open. Is there an easy to start a program through bash so that the program isn't inferior to bash? Thanks.

If you mean that when you start 'firefox', for instance, you cannot issue any more commands on the terminal - here's what you can do:

```
  % firefox &
  % gedit &
```

Using the ampersand at the end of a command detaches the application from the terminal and runs it in background. That way, your terminal is free to do more.

However, if the running application prints messages to the console, they will still be displayed on your terminal. To avoid them, use:

```
  % firefox > /dev/null 2>&1 &
```

---

### Post by skintythe1andonly on 2009-05-29
if you are going to be using console applications, you can use screen. It lets you multitask from the commandline but really only useful if your using console apps or say if you are logged in over ssh

---

