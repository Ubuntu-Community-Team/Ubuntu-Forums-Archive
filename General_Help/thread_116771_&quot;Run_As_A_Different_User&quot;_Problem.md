---
title: "&quot;Run As A Different User&quot; Problem"
date: 2006-01-13
forum: General Help
---

### Post by Illybey on 2006-01-13
Ok I know I am new at this but I need to run as "Root" to make folders and such. And this feature should let me run as root in the gui, right?

Strange thing is it doesn't want the root password, it says wrong password if I put in the root pass but if I put in the users pass then it doesn't get an error. But if I open up the file browser and try to move files around it says I don't have permission for that?

---

### Post by Mr_Grieves on 2006-01-13
First off.. why do you need to become root? That's 99% of the times not a good idea.
Use:
```

sudo mkdir <foldername>

```

If you now MUST (!!!!) become root.. then.

1) Make you're a password is set for the account. If it's not:
```

sudo passwd root

```

Then
```

su - root

```

---

### Post by Illybey on 2006-01-13
I did the passwd root and changed the password already and in the terminal I get the # but I don't know how to move stuff around in the gui very well yet.

---

### Post by hillbilly on 2006-01-13
For opening graphical applications as root, use "gksudo" instead of "sudo" !

---

### Post by Illybey on 2006-01-13
Ok here comes the stupid, taking up your time, question. How do I run gksudo?

I did do a sudo -s command on the terminal earlier and that gave me the # in the terminal mode. But when I put in gksudo it says, Error- Missing command to run.

---

### Post by Illybey on 2006-01-13
Wow it must have been really stupid to get no response :)

Well I am going to hang in there because I feel a Linux Explosion in the works and I would like to be in the know :)

---

### Post by yogiman_uk on 2006-01-13
Hi

I am afraid I can not help with your problem.

2 points to make here.

Point 1 I've never come across a distro that would not let me log into the GUI as root before? Why don't these people want us to access the system fully doesn't this stink of Microsoft!

There are too many so called Linux experts out there trying to make people look small because they don't know how to use the system.  Well guess what, all the time people take this stance Linux will never push Windows off the desktop and if you ask me that would be a shame.

So next time one of you so called linux experts decides to help someone just to make them look small, remember once upon a time you didn't know anything either!

I think I will just sit back and wait for annoyed linux guru's to sling brown stuff at me now!

Regards

Yogiman!

---

