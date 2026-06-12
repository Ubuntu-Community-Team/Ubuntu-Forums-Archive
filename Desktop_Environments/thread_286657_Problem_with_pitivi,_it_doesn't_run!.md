---
title: "Problem with pitivi, it doesn't run!"
date: 2006-10-28
forum: Desktop Environments
---

### Post by mdurham on 2006-10-28
I try to run pitivi on Edgy and get the following. Any clues as to what the problem might be?
> mike@stationedgy:~$ pitivi
The program 'pitivi' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 15 error_code 3 request_code 3 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
mike@stationedgy:~$ 


Cheers, Mike

---

### Post by jlx on 2006-10-29
Same problem here. Cinelerra hangs. Lives is a mess. Diva doesn't work. It is not possible video editing in Edgy.

---

### Post by JedTheHead on 2006-11-02
Same thing here.  Any ideas out there?

---

### Post by kritzikratzi on 2006-11-03
I'm having the exact same. 

I know it was always said that edgy wouldn't be focused on stability, but the amount of crashes, freezes and sound-not-working situations i get here are crazy...

---

### Post by uuwatti on 2006-11-05
, run it with the --sync command line
So, ```
pitivi --sync
``` should do the trick.

---

### Post by tvphil on 2006-11-29
O.k., that did work, but what a disappointment! This is one crude video editing software. Maybe I'm missing some plug-ins, but this makes Lives look good.All I see are source inputs, codec choices and output. No fading, mixing or text super choices to be found anywhere.If I am missing some plug-ins or anything else, please post them. I'd like to use this, but not the way I see it now.

---

### Post by mdurham on 2006-11-29
I agree with you tvphil, it's hard to imagine what it can be used for. Increasing forum traffic maybe?
Mike

---

### Post by jlx on 2006-11-30
I've edited some videos with main actor. It's the best video editor for linux. But you have to pay, although you can use the demo for ubuntu and it works perfect with edgy.

---

