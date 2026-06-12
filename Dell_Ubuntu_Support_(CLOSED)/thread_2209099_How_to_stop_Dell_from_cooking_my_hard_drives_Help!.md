---
title: "How to stop Dell from cooking my hard drives? Help!"
date: 2014-03-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MakOwner on 2014-03-03
I have a Dell Precision T7500, Dual Xeon 5639 with the onboard SAS 6iR controller.

The "optional" 3.5 drive slot in the front (attached to the "optical" SATA ports) runs the drive under load at a little over 100F.
The rear 4 drives attached to the LSI controller runs in excess if 115F.  Idling.  I just watched one last night exceed 120F while idling for a couple of hours.
Based on the slow, lazy way the fans run you'd thing the case was sitting in the Antarctic.
I have exchanged the chassis and still the drive heat issues remain - the case fans are real nice and quiet ... except for the bubbling from the drives boiling ...

Surely these things do more than incinerate hard drives??
How do I increase the fan speed for better airflow?

---

### Post by bcschmerker on 2014-03-03
After viewing photos of your model, I have identified a problem that will at least force major modifications to the case, at worst force the transfer of all internal hardware to another case design:  Being shoehorned transversely beneath the power supply, those hard drives most likely do NOT have fans anywhere near them!  This is a serious design flaw on the part of Dell Computer.  The photo that tipped off the problem indicates very little room to retrofit fans inboard of the forward hard drives, and massive amounts of air have to move to extract the heat.  I had to battte this problem in an eMachines®/Acer® EL1210-09 I was rebuilding due to a thermal failure of the original 3.5" hard drive's electronics, which required both downsizing to a new 2.5" hard drive on a shock mount of my own fabrication and cutting exhaust holes in the case cover to let the heat out.

Were I building a system of identical performance to the Precision T7500, the minimum case I would have used would be the Antec® Eleven Hundred&#8482;, which has provisions for two 120mm fans to blow air directly across up to six 3.5" hard drives.  Although Antec® markets a candidate for the hard-drive-cooling mission in the Tri-Cool&#8482; 120 DBB, I'd want a pair of Delta Electronics FFB1212VHE case fans, each of which is rated for 151.85 CFM @ 3200 RPM.

---

### Post by MakOwner on 2014-03-04
There are a LOT of fans in that case - including one sandwiched between the drives. Just speeding the freaking fans up will do the trick.  I hope.

---

### Post by Bucky Ball on 2014-03-04
Is the power supply a generic silver box that gets so hot you can't touch it? If so, that is not helping. They work great as heaters in winter but are hopeless, and dangerous, as PSUs. 

If you have a red hot 1000Watt silver box power supply, just another problem to contend with, if not now, then eventually.

---

### Post by MakOwner on 2014-03-04
I don't think it's the 1000 watt PS model, but I'm not sure.  PS doesn't feel all that hot, the fans just aren't moving any air.  I have foiund some information about the i8k package.
I'm going to try that in the morning to see if it will increase fan speed.

---

