---
title: "using octave under xwin ssh"
date: 2009-01-07
forum: Education &amp; Science
---

### Post by natanel on 2009-01-07
I installed cygwin with xwin

using xWin server and ssh to log into the ubuntu computer from my windows comuter

then running octave (over ubuntu)

this work great (faster then runing octave in cygwin and windows)

but how I can config the plot to be seen in the windows computer

how I tell cygwin or xWin server or ssh to plot over the windows computer 

for example I would like to see in my windows computer
a=[1 2 3 4];
plot(a);

also how I can config which to use from octave line gnuplot or plot_edit

many thanks

---

### Post by ssam on 2009-01-07
try using
```
ssh -X user@ubuntumachine
```
(note capital X)

between linux machines that sets up a tunnel for X, and sets the right $DISPLAY variables, so it may work for you.

---

### Post by natanel on 2009-01-08
can you give example how to set/define the DISPLAY

I am getting from octave

octave:1> a=[1 2 3 4];
octave:2> figure;plot(a);
X11 connection rejected because of wrong authentication.

gnuplot: unable to open display 'localhost:10.0'
gnuplot: X11 aborted.
X11 connection rejected because of wrong authentication.
octave:3> 
gnuplot: unable to open display 'localhost:10.0'
gnuplot: X11 aborted.


thanks

---

### Post by ssam on 2009-01-08
that display looks good for going through the tunnel.

in linux to linux situations i have fixed the authentication issue by making sure that xauth is installed.

there is a less secure method where you allow the X11 to travel over the network unencrypted, but this will allow anyone on the network to eavesdrop, or monitor keystrokes.

you open up the xserver to outside connections using xhost (i cant remember the options), then on the remote manchine

export DISPLAY=localmanchineIP:0

---

