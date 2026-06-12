---
title: "Problems playing CDs and DVDs"
date: 2009-05-02
forum: General Help
---

### Post by Kerubu on 2009-05-02
Hello,

I recently moved from Ubuntu 8.04 to 8.10.

In 8.04 Rhythmbox could play CDs ok(ish) but ever since I have moved to 8.10, whenever I try to play a DVD, totem (or whatever DVD playing software I choose) opens but then crashes (I assume crash because no error message is thrown, the window just closes).

The same thing happens when I try to play a music CD.. Rhythmbox opens but then closes.

So,

1) Is there an error log where software crashes are reported, and if so where is it on my computer ?

2) Anyone know how I can resolve this problem ?

Kerubu

---

### Post by delcypher on 2009-05-02
Run the particular application from the terminal and redirect stderror messages to a file called errorlog

e.g. to run rhythmbox with errors going to errorlog ```
rhythmbox 2> errorlog
```

You could try running rhythmbox in debugging mode too (this produces a lot of output)

e.g. to run rhythmbox with errors going to errorlog ```
rhythmbox -d 2> errorlog
```

You could try out the other applications in a similar manner.

---

### Post by Kerubu on 2009-05-02
> **delcypher said:**
> Run the particular application from the terminal and redirect stderror messages to a file called errorlog

e.g. to run rhythmbox with errors going to errorlog ```
rhythmbox 2> errorlog
```

You could try running rhythmbox in debugging mode too (this produces a lot of output)

e.g. to run rhythmbox with errors going to errorlog ```
rhythmbox -d 2> errorlog
```

You could try out the other applications in a similar manner.

Thanks for that will try it and see what happens

---

