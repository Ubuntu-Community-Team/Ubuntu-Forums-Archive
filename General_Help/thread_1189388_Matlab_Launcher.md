---
title: "Matlab Launcher"
date: 2009-06-16
forum: General Help
---

### Post by nmaster on 2009-06-16
So I as making a launcher for matlab.  I go edit menus, yadda yadda yadda, I say the command is matlab -glnx86.

When I click on the launcher either nothing happens, or if I ask it to run in a terminal, the terminal will pop up for moment and then close.

It would be nice to have a launcher.  Can anyone help?

---

### Post by synapsys on 2009-06-16
Not familiar with matlab. Have you tried using sudo before it? Have you tried just matlab without the options? How do you normally start it up? Maybe try putting a '&' at the end so the terminal will hold and you can see some error messages.

---

### Post by nmaster on 2009-06-17
I usually run it from the terminal with "matlab -glnx86" because I installed the 32-bit version but I have 64-bit Jaunty.  None of your suggestions worked.  I'm not sure if its a matlab problem or something else.  I tried making an alias for matlab so that I wouldn't have to put the arguments, but that doesn't help with the launcher either.

Does anyone else have a suggestion?

---

### Post by Leporello on 2009-06-17
Try matlab -desktop as the launcher command. Or maybe matlab -glnx86 -desktop. I'm not entirely sure why this is necessary but that's the way it's set up on my machine, and I remember having the same problem you're describing.

---

### Post by nmaster on 2009-06-17
using matlab -glnx86 -desktop worked.  I'm not sure why.  It would be good to know.

Did you ever have problems with Matlab figures displaying video?  I have a figure that displays plots and turns them into a movie.  It used to show up, but now it doesn't.  I get this weird flickering.  The only thing I've done since then is run the Mac4Lin script.  I guess this isn't what I initially asked about, but if you can help it would be good.  Otherwise, I'll just make a new thread.

Thanks for the help with the launcher Leporello!

---

