---
title: "Funky Gnome calculator"
date: 2005-06-02
forum: Desktop Environments
---

### Post by thinusp on 2005-06-02
Hi there

I think there may be a small problem with the exponential function in the gnome calculator. Would some be so kind as to verify what I found?

according to my c library and several other online calculators:
```
exp(0.315506) = 1.370952
``` 
```
exp(0.158041) = 1.171214
```

Gnome calculator says:
```
exp(0.315506) = 2.299377472
```
```
exp(0.158041) = 1.517522768
```

I checked that the calculator is set to decimal etc etc.

Anyone else have this bug?

Cheers
T

---

### Post by Alexander Kirillov on 2005-06-02
[QUOTE=thinusp]Hi there

I think there may be a small problem with the exponential function in the gnome calculator. Would some be so kind as to verify what I found?

according to my c library and several other online calculators:
```
exp(0.315506) = 1.370952
``` 
```
exp(0.158041) = 1.171214
```

Gnome calculator says:
```
exp(0.315506) = 2.299377472
```
```
exp(0.158041) = 1.517522768
```

I checked that the calculator is set to decimal etc etc.

Anyone else have this bug?

Cheers
T[/QUOTE]
 I can confirm that - but more than that, 
exp(1)=14
exp(2)=196
so it seems that the GNOME calculator assumes e=14. This is  a MAJOR bug. I've filed it in bugzilla as 


[bug 306277](http://bugzilla.gnome.org/show_bug.cgi?id=306277)

---

### Post by thinusp on 2005-06-02
thanx

I was wondering if it was gcacltool or my PC ;)

Cheers
T

---

### Post by shakin on 2005-06-02
[QUOTE=thinusp]thanx

I was wondering if it was gcacltool or my PC ;)

Cheers
T[/QUOTE]

Your PC? Are you running a 90Mhz Pentium perhaps? :)

---

### Post by thinusp on 2005-06-02
hehehe, nope P4, But you never know ;)

Cheers
T

---

### Post by duff on 2005-06-02
hmm.. e^0.315506 gave me 1.370952838, same as `bc`
```
# echo "e(0.315506)" | bc -l
1.37095283761578820958
```

What version are you running?, I've got Gcalctool 5.6.14

---

### Post by Alexander Kirillov on 2005-06-02
[QUOTE=duff]hmm.. e^0.315506 gave me 1.370952838, same as `bc`
```
# echo "e(0.315506)" | bc -l
1.37095283761578820958
```

What version are you running?, I've got Gcalctool 5.6.14[/QUOTE]
 I've got 5.5.41 (I believe this is the default one in Hoary)

---

### Post by thinusp on 2005-06-02
hmm, yep, 5.5.41 seems to be the faulty one.

---

### Post by Alexander Kirillov on 2005-06-02
Turns out this bug had been reported a few times and has been fixed already. It seems somehow it was treating e as a hex number...

---

### Post by YaAqoB on 2005-06-19
IS there another Calculator that I can use with Ubuntu?
The standard one don't seem to work to well for me.
For example. If I go

100+12.5% I get 112.5 Which is correct.

200+12.5% I get 212.50 Which is not correct.

I'm starting to think the % button is not working.

---

### Post by thinusp on 2005-06-20
Isn't it time to update the gnome package that contains the calctool? I know there's a new version that supposedly fixes these inconsistensies.

Cheers
T

---

