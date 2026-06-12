---
title: "conky question"
date: 2009-04-26
forum: General Help
---

### Post by groovomata on 2009-04-26
Hello All, 
I've been fiddling a bit with conky and I really like it. I've got mine set up so that it doesn't draw it's own window but is forked to the desktop. The only thing is, when I click my 'show desktop' icon, or press <Ctrl><Alt>D to show my desktop, conky minimizes as well. Does anyone know how to  stop conky from minimizing or to more securely embed it into the desktop background?
I've included a screenshot to give an idea of what it looks like.
Thanks in advance,
Erik.

---

### Post by groovomata on 2009-04-26
As usual, I solved my post. The answer is:
```
# Create own window instead of using desktop (required in nautilus)
own_window no
```
I had this set to yes before.

---

### Post by Rahul Buttar on 2009-04-27
I'm trying to do a similar thing for an embedded terminal.  Where did you put this code:

# Create own window instead of using desktop (required in nautilus)
own_window no
Was it maybe in a shell script you use to open conky?

---

### Post by kpkeerthi on 2009-04-27
> **Rahul Buttar said:**
> I'm trying to do a similar thing for an embedded terminal.  Where did you put this code:

in ~/.conkyrc

> 
# Create own window instead of using desktop (required in nautilus)
own_window no
Was it maybe in a shell script you use to open conky?
To start conky, type **conky** at the shell prompt.

---

### Post by Rahul Buttar on 2009-04-27
I'm sorry I misstated my question.

How would I edit a terminal configuration file to have: "own_window no"?

I'd like to exclude my embedded terminal from the show desktop button.

---

### Post by kpkeerthi on 2009-04-27
I assume you are using compiz. This [link]("http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html") has the instructions you need.

You also need compizconfig-settings-manager to tweak the settings.
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Rahul Buttar on 2009-04-27
Well I already did all that and successfully embedded a terminal, I'm trying to find out if there is a gnome terminal RC file that I can modify so that it doesn't have it's own window.

So far all I've found is a gconf.xml under: .gconf/gnome-terminal/profiles/profile0

Can I maybe modify this XML file with "own_window no"?

Or maybe create an RC file for this instance of the gnome terminal?

Or maybe there is a .bashrc file that I can modify?

Thank you so much for your help.  I'm very much a beginner.

---

### Post by Rahul Buttar on 2009-04-27
Never mind, the solution was much simpler than I thought.  All it required was unchecking "Hide Skip Taskbar Windows" under general settings in compiz.

Thanks for your patience.

---

