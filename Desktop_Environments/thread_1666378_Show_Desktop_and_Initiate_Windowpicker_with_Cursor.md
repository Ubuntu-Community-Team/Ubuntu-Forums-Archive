---
title: "Show Desktop and Initiate Windowpicker with Cursor on Corner + Click"
date: 2011-01-13
forum: Desktop Environments
---

### Post by f1ckratte on 2011-01-13
Hi Guys

I'm using my machine as a htpc and have got a remote with a 3D sensor as mouse. It often happens that i accidentally move to the bottem left or right with the mouse and as consequence desktop will show or window picker will be initated. This can be very annoying when watching a film or visualization. I know where to edit this options in my compiz-config utility, but i dont know what to write... 

BottomLeft + Button1

?

I would be glad if someone helps me.

---

### Post by stinkeye on 2011-01-14
Use the mouse for initiation.


You could also increase the edge trigger delay in
General Options.

---

### Post by stinkeye on 2011-01-14
2 too bad

---

### Post by f1ckratte on 2011-01-14
Tripple post -.-

---

### Post by f1ckratte on 2011-01-14
-

---

### Post by f1ckratte on 2011-01-14
Thanks.
This works for initiating window picker. For Show Desktop there is no such option. If I edit it manually a window appears with the Title error occured and it says: """ is not a valid edge mask".

I guess this has to be changed manually in compiz config file?
if yes could you please tell how?



OMG

---

### Post by stinkeye on 2011-01-14
Disable the show desktop corner and set your own shortcut
in the ccsm commands plugin, using xdotool.

```
sudo apt-get install xdotool
```

Open **CCSM > Commands** and add 
```
xdotool key super+d
```
to one of the command boxes.

Then go to the button tab and choose the corresponding command with corner plus mouse button 1

**NOTE:** super+d IS FOR Maverick.
ctrl+alt+d before I think.

---

### Post by f1ckratte on 2011-01-17
thanks, great help.
thats why i love linux comunity :)

---

### Post by apochry on 2011-03-29
Got here trying to initiate 'show desktop' by clicking a corner. :)
Thanks stinkeye!

Izzo

---

