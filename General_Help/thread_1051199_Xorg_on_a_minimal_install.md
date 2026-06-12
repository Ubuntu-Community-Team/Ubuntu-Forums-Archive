---
title: "Xorg on a minimal install"
date: 2009-01-26
forum: General Help
---

### Post by Naiki Muliaina on 2009-01-26
When i use the alternative CD and install a the minimal Ubuntu install, i use the following line for an interface and starting point.

```
sudp apt-get install xorg xfce synaptic gdm
```

I then start x, install the nvidia 177 driver. From there its downhill as Xorgs file isnt configured properly. I generate a xorg a file, that works, but still the nvidia driver wont activate. Ive done this 3 or 4 times now with the same outcome. Im going to have another go tonight. Before i start, is there something fundamental im missing? Something im not installing between xorg and the nvidia driver? 

Any response gratefully recieved :)

---

### Post by kerry_s on 2009-01-26
why do you need to startx if you have gdm?
the line looks good, so it must be the driver install, how are you doing that?

---

### Post by bodhi.zazen on 2009-01-26
> **Naiki Muliaina said:**
> When i use the alternative CD and install a the minimal Ubuntu install, i use the following line for an interface and starting point.

```
sudp apt-get install xorg xfce synaptic gdm
```I then start x, install the nvidia 177 driver. From there its downhill as Xorgs file isnt configured properly. I generate a xorg a file, that works, but still the nvidia driver wont activate. Ive done this 3 or 4 times now with the same outcome. Im going to have another go tonight. Before i start, is there something fundamental im missing? Something im not installing between xorg and the nvidia driver? 

Any response gratefully recieved :)

I can not determine your problem from your description.

What I do, from X, is run```
gksu nvidia-settings
```

Set up X -> save settings.

The trick is in that last step, where you save the settings. In the pop up dialog box there is an option to merge your settings with the existing xorg, UNSELECT that option (you want a new file, not a merged one).

Or perhaps I am misunderstanding you ?

---

### Post by Naiki Muliaina on 2009-01-26
Did the trick ^^ Thankyou!

I appear to have lost the thanks button... Ill give you thanks when it reappears ^^

---

