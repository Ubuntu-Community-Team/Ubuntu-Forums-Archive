---
title: "QtOctave - set(atom,'Xdata',X(i)) - 10,000+ times"
date: 2009-05-28
forum: General Help
---

### Post by Drokles on 2009-05-28
Hello all.

I was fiddling about with a matlab code that animates phonons interpreted via Hooke's Law, which means a few hundred coupled differential equations, and I've tried translating it to QtOctave.

My problem is using the set command which, as I found out, works very differently from the matlab equivalent. Right now the plot window that hosts the animation keeps opening and closing, and it will probably do that for a few hours since it takes just about 0.3 seconds each time when it should only pause for 0.00005 seconds, and I'm letting it do so in a 10,000+ loop :D.

Is there a better command to use? and is there any difference betwen set() and plot()?

Also, if QtOctave has some equivalent of ode45() it would be great. My code looks like a mess because I had to teach it how to solve all those differential equations.

Good luck!
~ Drokles

Edit:

```

for i=1:length(t)
    set(atom,'Xdata',X(i,n))
    pause dt/10
end

```n being the number of atoms and t being the corresponding times.

---

### Post by Drokles on 2009-05-28
I hope I put this in the right place?

---

