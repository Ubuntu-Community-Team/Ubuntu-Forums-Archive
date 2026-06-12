---
title: "GPL and Linux training?"
date: 2007-06-27
forum: Education &amp; Science
---

### Post by drbongo on 2007-06-27
Hi, I am an enthusiastic Linux convert, but I am ashamed to say that I earn my living teaching people how to use Microsoft software at a leading educational institution in the UK! The college can't see the merits of Linux because they don't see how it can bring in any income and I am trying to convince them that we should offer Linux workshops/training to individuals/institutions who would like to know about open source software and operating systems initially, and in the long run perhaps offer installation/network support to interested parties. My question is this...

Does the GPL allow us to charge people/institutions for training using established Linux distributions such as Ubuntu, SUSE and Fedora etc and provide them with copies of the software for free at the end of the day? And are we allowed to offer technical support with the installation and running of these systems afterwards? Or would we need to remove all the branding etc and produce our own distro etc?

Any advice on this would be gratefully accepted as I do not want to get this process underway only to find that there are legal restrictions on doing this.

drbongo

---

### Post by euler_fan on 2007-06-27
I'm not a lawyer or GPL expert, but I'd say the following:

1) Canonical makes its money selling support services and Ubuntu is under the GPL (it might be the Limited GPL, not sure). Ergo, I would presume there are no problems with selling support services so long as you do not sell the software itself (merely cover the cost of making copies). Not sure how to handle the whole as part of a class thing--maybe put together a disk and sell it through the university bookstore for the cost of procuring the disks.

2) All other issues aside, unless there is software which is not part of the base distribution for Ubuntu that you would want/need for the class, I would say there is no need for a custom disk. If, however, you were doing one for say, web development, then it might behoove you to make one just to make sure everything your students will need is on the disk already. You can always show them how to download additional tools they might like better (for instance, Bluefish verses Screem).

3) If there are really deep issues where you would be in conflict with the GPL, look at a BSD based distro. By reputation it sounds like a completely open license that allows users to do as they will with more or less no questions asked (including resale?).

@Everyone out there: please correct anything I got wrong on this. I'm curious too :)

---

### Post by LaserJock on 2007-06-27
> **euler_fan said:**
> I'm not a lawyer or GPL expert, but I'd say the following:

1) Canonical makes its money selling support services and Ubuntu is under the GPL (it might be the Limited GPL, not sure). Ergo, I would presume there are no problems with selling support services so long as you do not sell the software itself (merely cover the cost of making copies). Not sure how to handle the whole as part of a class thing--maybe put together a disk and sell it through the university bookstore for the cost of procuring the disks.

2) All other issues aside, unless there is software which is not part of the base distribution for Ubuntu that you would want/need for the class, I would say there is no need for a custom disk. If, however, you were doing one for say, web development, then it might behoove you to make one just to make sure everything your students will need is on the disk already. You can always show them how to download additional tools they might like better (for instance, Bluefish verses Screem).

3) If there are really deep issues where you would be in conflict with the GPL, look at a BSD based distro. By reputation it sounds like a completely open license that allows users to do as they will with more or less no questions asked (including resale?).

@Everyone out there: please correct anything I got wrong on this. I'm curious too :)

1)  Ubuntu, as a distro, is not under the GPL but much of the software is licensed under the GPL. There are a lot of other licenses though. But in fact it doesn't really matter. The GPL allows you to sell the software for whatever you like, as long as you make the source code available as well. It's perfectly fine to make money selling GPL or Ubuntu software. There are several companies (including Amazon) that sell Ubuntu CDs. For more info on the GPL you should check out [http://www.fsf.org/licensing/licenses/gpl-faq.html](http://www.fsf.org/licensing/licenses/gpl-faq.html). As long as you stick to the Main and Universe repositories (i.e. not Multiverse) you should be fine selling or making money from it. And on top of that, going back to the original question, selling training is a great way to make money with Linux. In fact, Canonical has a Training Partner program ([http://www.ubuntu.com/partners/trainingpartner](http://www.ubuntu.com/partners/trainingpartner)) starting for training Ubuntu Certified Users and Ubuntu Certified Professionals.

2) Doing an Ubuntu remix is fairly easy to do these days with Reconstructor or Ubuntu Customization Kit (UCK) . I was thinking of making a custom chemistry disk for my uni.

3) BSD distros often have GPL'd software as well. The BSD license (or MIT license) is a more liberal license than the GPL but the BSD license is not necessarily the same as the license of all the software in a BSD distro.

---

### Post by az on 2007-06-27
> **drbongo said:**
> 

Does the GPL allow us to charge people/institutions for training using established Linux distributions such as Ubuntu, SUSE and Fedora etc and provide them with copies of the software for free at the end of the day? 

Yes, so long as those distros a re free to distribute.  Some distros like Linspire and Xandrox are non-free and not distributed under only the GPL.  If you are talking about Ubuntu and other free-libre distros, yes.

> **drbongo said:**
> 
And are we allowed to offer technical support with the installation and running of these systems afterwards? 

Yes, absolutely.

> **drbongo said:**
> 
Or would we need to remove all the branding etc and produce our own distro etc?

You only need to remove branding when your work conflicts with Canonical's Ubuntu trademark.  If you are making a derivative of Ubuntu, then it's not longer Ubuntu and you cannot pretend that it is.

But distributing Ubuntu to your friends and clients does not violate the trademark because it is what it is.

> **drbongo said:**
> 
Any advice on this would be gratefully accepted as I do not want to get this process underway only to find that there are legal restrictions on doing this.

drbongo

As far as the software goes, it's simple.  The GPL says that:

1-  You can use the software for any purpose.
2-  You can redistribute the software
3-  You have obtained the source code with your copy and must provide it with any copies you distribute (Canonical provides the source for Ubuntu, so don't worry about that.)
4-  If you modify the program (because you have the source and are encouraged to modify it as you wish) if you redistriute the program, you must make available to modified source code.

That's it.  It's pretty simple.

---

