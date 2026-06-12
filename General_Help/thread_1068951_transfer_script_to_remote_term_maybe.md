---
title: "transfer script to remote term? maybe"
date: 2009-02-13
forum: General Help
---

### Post by micahmills on 2009-02-13
ok so i have a Left 4 Dead dedicated server running out of my house, what i want to be able to do is log into my server with portaPuTTy from my friends house and have the game script show up in the PuTTy terminal on my laptop, is this possible, (yes i'm kinda a n0ob to linux). I know i can log in and access files and such because i already do this, so i guess the main question is how do i get a game server script to show up in a remote login terminal?

kthnxbye!

---

### Post by geirha on 2009-02-13
If I understand you correctly, you want to be able to log in from one computer, start a script that will run "for ever", and then be able to log in from another computer and look at it's output?

If so you'll want to learn about the screen command.
Log in and type ```
screen
```

You'll be taken to a new shell. Start the script in there, then hit Ctrl+a+d. This detaches the screen, with the script still running in the background. Now you can log in at any time and reattach the screen with 
```
screen -r
```
If you ever forget to detach from another machine, you can do 
```
screen -dr
``` 
to detach it and reattach it at your current terminal.

Hope this helps, and search for guides on the screen command. It's very handy to know it's features.

---

### Post by micahmills on 2009-02-14
yes i think thats exactly what i'm looking for, thank you. I'll try it as soon as i get the chance.

---

