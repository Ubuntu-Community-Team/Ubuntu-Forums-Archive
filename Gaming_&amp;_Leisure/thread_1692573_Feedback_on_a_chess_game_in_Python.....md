---
title: "Feedback on a chess game in Python...."
date: 2011-02-21
forum: Gaming &amp; Leisure
---

### Post by alexkiro on 2011-02-21
I have created a chess game in Python using Tkinter module, although i know this isn't the best choice, but i'm not yet familiar with more complicated programming tools... But anyways ... you can find it here:

[http://students.info.uaic.ro/~alexandru.chirila]("http://students.info.uaic.ro/~alexandru.chirila")

I would appreciate any kind of critic, feedback and suggestions....

thanks a lot ...

---

### Post by tastygrue on 2011-02-23
Okay, so when I do ./chess.sh, I get:
```
./chess.sh: line 2: ./dist/chess: cannot execute binary file
```Is there a way around this?

---

### Post by alexkiro on 2011-02-24
Sorry i don't see why it won't work...

Try these:
-go to dist folder, give permissions to be executed to the binary file chess and then run, the sh file is more of a shortcut...

- or better yet just download the source, install python and python-tk and run it

thanks again...

---

### Post by lykeion on 2011-02-24
It works fine for me and it looks okay, though personally I find Tkinter not the prettiest GUI toolkit. I think you need to add some very special features to make it stand out from other chess applications like PyChess (if that's the goal for you).

---

### Post by tastygrue on 2011-02-24
Okay, so what I found:
Castling works great for both queenside and kingside;
En Passant needs to be implemented;
The program doesn't recognise a checkmate.
Other than that, I think this is quite a fine chess program, although I have to admit that I haven't had much experience with other chess programs in the past.

---

### Post by alexkiro on 2011-02-28
The En passant rule should really break the whole code logic and i'm afraid to start, but i will soon...

The program can recognize a check mate, but it has some loop holes that could really break the game, i have to cover all of them first and after it will be implemented 

I'm not trying to compete with any other similar programs, i mostly compete with myself... although you are right some special features may make it stand up, but i don't have any great revolutionary ideas... yet...

I'm trying to make it playable in network, with one computer hosting the game and another connecting to it...

Could you guys recommend another GUI toolkit, Tkinter is relatively simple to use... but as you say it's fairly ugly.

---

### Post by sofiamarcella on 2011-02-28
Why don't work in my...... what happen :-({|=#-o    [IMG]http://freeimagestocks.com/content/5/love.gif[/IMG]

---

### Post by alexkiro on 2011-03-07
> **sofiamarcella said:**
> Why don't work in my...... what happen :-({|=#-o    [IMG]http://freeimagestocks.com/content/5/love.gif[/IMG]

you have to be more specific

---

### Post by Lobais on 2011-03-25
Also remember, that you can always participate in the other chess clients out there. That way you will reach a larger base of users.

---

