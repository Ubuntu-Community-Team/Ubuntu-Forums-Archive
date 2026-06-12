---
title: "Simple newb question"
date: 2006-06-27
forum: Desktop Environments
---

### Post by Gorbachev on 2006-06-27
So, I have Wolfenstein ET installed. I want to install the TCE mod. I can't simply paste "tcetest" folder, which I extracted to my desktop, into the proper place (wolf et installation path). It wont let me. I don't have permission.

Why not?

How do I get it?

I'm the admin of my computer, I think I should have permission! :-?

---

### Post by Gorbachev on 2006-06-27
Since I've got this thread already going with no replies yet.... I'll add another question.

When setting up Evolution Mail..  how would I go about setting it up for a regular free hotmail account? I give it my email address..

[email]crazyxxxxxx@hotmail.com[/email] (fake)
hit Forward

What kind of Server type do I select?

Fill me in on everything I could ever possibly need to know, since I haven't been past this part yet.

Thanks :)


Edit: I just filled it in with fake crap, since all I really wanted was the calender function of it.

If anyone knows of a free calender app to set appointments and such, I'd much rather use that than this thing :?

Edit: I think I'll stick with Evolution since it integrates with Ubuntu's clock in the top right.

Thanks anyway :o

---

### Post by shawnrgr on 2006-06-27
[QUOTE=Gorbachev]So, I have Wolfenstein ET installed. I want to install the TCE mod. I can't simply paste "tcetest" folder, which I extracted to my desktop, into the proper place (wolf et installation path). It wont let me. I don't have permission.

Why not?

How do I get it?

I'm the admin of my computer, I think I should have permission! :-?[/QUOTE]

just because you are the only user or the "main" user who set up the computer, doesn't mean your the admin. you need to move the folder as root. place "sudo" before the mv command. the password should be your user password.

---

### Post by Gorbachev on 2006-06-27
Well, I wasn't using the terminal to move it.. I guess I'll have to figure out how to.

I suppose you could tell me, but I like to learn *some* of these things on my own ;)

So, thanks.

---

### Post by Gorbachev on 2006-06-27
Ok.. so, I need to find out how to do this. I'm stuck!

mv: cannot stat `/home/gorbachev/desktop/tcetest': No such file or directory

I happen to know it exsist.. so, perhaps someone tell me what I'm doing wrong.

---

### Post by dmizer on 2006-06-27
[QUOTE=Gorbachev]Ok.. so, I need to find out how to do this. I'm stuck!

mv: cannot stat `/home/gorbachev/desktop/tcetest': No such file or directory

I happen to know it exsist.. so, perhaps someone tell me what I'm doing wrong.[/QUOTE]
"desktop" is different than "Desktop".

your path name should read /home/gorbachev/Desktop/tcetest

---

