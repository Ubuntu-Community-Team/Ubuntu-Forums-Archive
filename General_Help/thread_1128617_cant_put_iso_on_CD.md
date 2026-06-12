---
title: "cant put iso on CD"
date: 2009-04-17
forum: General Help
---

### Post by JakeHinojosa on 2009-04-17
ive tried to put an iso on a cd. ive tried about 3 different programs like gnomebaker, k3b, and brasero. neither has sucessfully written it onto a cd. is it a problem with my computer? or could it be a problem with ubuntu?

---

### Post by lisati on 2009-04-17
You might find some helpful tips here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Comhra on 2009-04-17
I find that burning an ISO is best done with the Nautilus burner at the lowest possible speed which is 1 x.  Doesn't take that long and it's always worked for me.

---

### Post by Daisuke_Aramaki on 2009-04-17
check the md5sum of the downloaded iso against the sum which you should get from the place where you downloaded the iso. If there is a mismatch, due to broken downloads, you might get an error. Can you please let us know what error message you get, and is it uniform with the different burning programs you use?

---

### Post by Slim Odds on 2009-04-17
> **Comhra said:**
> I find that burning an ISO is best done with the Nautilus burner at the lowest possible speed which is 1 x.  Doesn't take that long and it's always worked for me.

There is absolutely no reason to burn at 1X.

There are a number of good burners in linux, but I like to use ImgBurn (using WINE).

Just make you configure it for ASPI (in the I/O settings).

---

### Post by boof1988 on 2009-04-18
Another option...

If the md5sum of the file passes, if you are not afraid of using CLI, and you can navigate into the directory containing the iso file.  The following is one way you can burn the iso.  [Note that you should use the actual filename of the iso in place of *filename.iso* in the below example]

```
cdrecord -v dev=/dev/cdrom filename.iso
```

If you don't have cdrecord installed, it can be installed using...

```
sudo apt-get install cdrecord
```

---

### Post by ToddAndMargo on 2009-04-18
What burner are you using?  

I almost went nuts with my Plextor burner.  When I changed to an Optiarc, happy camping returned.  I could even do an md5sum on a freshly burned disc without 1) ejecting and injecting it and 2) with virtual machines running.  They are a class act  -- cheap too!

[http://www.sonynec-optiarc.com/products/hhid_dvdrw/ad7220.html](http://www.sonynec-optiarc.com/products/hhid_dvdrw/ad7220.html)

HTH,
-T

---

### Post by Yashiro on 2009-04-18
Ubuntu needs an overly large CD. It won't fit on 'old' 650Mb discs.
Probably not the issue you're encountering but just thought I'd mention it.

---

