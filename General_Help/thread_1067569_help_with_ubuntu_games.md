---
title: "help with ubuntu games"
date: 2009-02-12
forum: General Help
---

### Post by Adrenochrom3 on 2009-02-12
ok so i need help with this problem i am having. i downloaded Neverball, and tremulous on to my laptop with the newest version of ubuntu. 

And

Well for some reason when i go to play neverball, the graphics are all messed up. but i can still play it, it doesnt look the way its supposed to, but its playable. and when i go to play tremulous i cant even play the game cause after a few seconds the menus disappear and i cant see the mouse, and it makes it reall hard to exit the game (it starts in full screen...)

what i would like to know is, is there any way to fix this? or am i not going to be able to play games? do i need an emulator, or some other packages to help the games out?

---

### Post by nealien on 2009-02-12
try updating ure graphics drivers.  other than that i got nothin...  lol

someone get this guy a fresh cup of ubuntu!

---

### Post by jonlemur on 2009-02-12
Are you running compiz?  I've had problems before with games running while I was using compiz.  If that's the case, try Alt+F2, metacity --replace.  Then try the games again.

---

### Post by Adrenochrom3 on 2009-02-12
yea im running compiz.

---

### Post by jonlemur on 2009-02-12
Then I would try switching to metacity and see if that's the problem.  In a terminal, run ```
metacity --replace
```

---

### Post by Adrenochrom3 on 2009-02-13
well i tried that, and i assume it turned off compiz. but firefox wouldnt close, and when i closed the terminal the task bar showed that it was still open. so i restarted my computer, and everything was back to normal.

---

### Post by Cresho on 2009-02-13
Turn off compiz and then start the game.  after the game is over, restart compiz.

You should learn now how to create scripts to get it working right!

turn on
```
#!/bin/bash
#Script Compiz/on/off

# Compiz off;
killall compiz.real &
metacity --replace &

#run game;
neverball

#Compiz on;
compiz --replace &
metacity --replace &
```

After you close the game, it will turn on on compiz automatically.

create a file and use text editor to put the code in it.  call the file "neverball.sh" no quotes.  now right click on it and give it permission "allow execute".

you can double click the file and try it.  say run.

If you want to add it in your start, right click on your start menu and edit and redirect the neverball command with the sh file.  I created a Installed_programs folder in my username directory because i have well over 1000 scripts doing odd jobs.  When I clean update it, those commands are there still.

---

### Post by jonlemur on 2009-02-13
Under System->Preference->Appearance, try turning off Visual Effects.  I think that takes you back to metacity.

---

### Post by Adrenochrom3 on 2009-02-15
thanks Cresho that worked beautifuly. i just changed the command for neverball to open that file instead of just adding a new command for it.

---

