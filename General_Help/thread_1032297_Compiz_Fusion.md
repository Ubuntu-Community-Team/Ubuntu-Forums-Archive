---
title: "Compiz Fusion?"
date: 2009-01-06
forum: General Help
---

### Post by Lisimelis on 2009-01-06
Hallo to all from Greece! I installed Ubuntu 8.10 on my Toshiba Satellite laptop. It is a Pentium4 and has 512 Ram. Everything worked lovely! I even installed some Screenlets and the Cairo dock! I was amazed! Then I saw the 20th issue of Full Circle magazine. In page 35 there is someone that has enabled compiz fusion on an eeepc. I thought it would be great to have all these effects (cube etc.) Needles to say i tried to and failed to enable them from the System/Preferences/Appearance menu. I download and installed CompizConfig Settings Manager but achieved nothing. My card is this

01:00.0 VGA compatible controller [0300]: S3 Inc. Supersavage IX/C SDR [5333:8c2e] (rev 85)

Is it impossible to have CompizFusion with this card or am i doing something wrong? 

Thanks in advance 
Yiannis.

---

### Post by overdrank on 2009-01-06
> **Lisimelis said:**
> 
01:00.0 VGA compatible controller [0300]: S3 Inc. Supersavage IX/C SDR [5333:8c2e] (rev 85)

Is it impossible to have CompizFusion with this card or am i doing something wrong? 

Thanks in advance 
Yiannis.

Hi and the SIS graphics do not support the 3d effects that well. But you may look here [Compiz-check]("http://ubuntuforums.org/showthread.php?t=799070")

---

### Post by bixejo on 2009-01-07
> **Lisimelis said:**
> Hallo to all from Greece! I installed Ubuntu 8.10 on my Toshiba Satellite laptop. It is a Pentium4 and has 512 Ram. Everything worked lovely! I even installed some Screenlets and the Cairo dock! I was amazed! Then I saw the 20th issue of Full Circle magazine. In page 35 there is someone that has enabled compiz fusion on an eeepc. I thought it would be great to have all these effects (cube etc.) Needles to say i tried to and failed to enable them from the System/Preferences/Appearance menu. I download and installed CompizConfig Settings Manager but achieved nothing. My card is this

01:00.0 VGA compatible controller [0300]: S3 Inc. Supersavage IX/C SDR [5333:8c2e] (rev 85)

Is it impossible to have CompizFusion with this card or am i doing something wrong? 

Thanks in advance 
Yiannis.

Hi there.

Did you install a 64bits distro?

If so, you should change a few lines in the compiz launching script. This happens since 7.10, and cannot figure out why it has not been fixed since then. Let me know whether this is your case and I'll drop here more instructions.

Regards,

---

### Post by Forlong on 2009-01-07
> **Lisimelis said:**
> My card is this

01:00.0 VGA compatible controller [0300]: S3 Inc. Supersavage IX/C SDR [5333:8c2e] (rev 85)

Is it impossible to have CompizFusion with this card
Yes, I'm afraid, that's the case: [http://bugs.launchpad.net/bugs/139953](http://bugs.launchpad.net/bugs/139953)

---

### Post by binbash on 2009-01-08
you can't run compiz-fusion with that card

---

### Post by Lisimelis on 2009-01-12
bixejo

I think i have the 32 bit edition on my laptop.

---

### Post by bixejo on 2009-01-12
> **Lisimelis said:**
> bixejo

I think i have the 32 bit edition on my laptop.
Well, buddy, looks like your problem is actually not that easy to circumvent, as it can be seen in Forlong's post link.

Sorry.

---

