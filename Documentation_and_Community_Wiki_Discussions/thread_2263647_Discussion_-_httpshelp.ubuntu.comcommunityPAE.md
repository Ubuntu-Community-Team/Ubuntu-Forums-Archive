---
title: "Discussion - https://help.ubuntu.com/community/PAE"
date: 2015-02-02
forum: Documentation and Community Wiki Discussions
---

### Post by mörgæs on 2015-02-02
Which page is better? 

Please compare the present version 
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

against the pages

[https://help.ubuntu.com/community/PAE?action=recall&rev=43](https://help.ubuntu.com/community/PAE?action=recall&rev=43)
and
[https://help.ubuntu.com/community/PAE/PentiumM?action=recall&rev=10](https://help.ubuntu.com/community/PAE/PentiumM?action=recall&rev=10)


Which is more helpful for a beginner?
Easy to understand?
Complete? 

- and other criteria you find relevant.

---

### Post by sudodus on 2015-02-02
> **mörgæs said:**
> Which page is better? 

Please compare the present version 
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

I think this page is more useful for beginners and average users, who need help to run Lubuntu or Xubuntu 14.04.1 LTS in their old laptop with Pentium M or Celeron M processors.
> 
against the pages

[https://help.ubuntu.com/community/PAE?action=recall&rev=43](https://help.ubuntu.com/community/PAE?action=recall&rev=43)
and
[https://help.ubuntu.com/community/PAE/PentiumM?action=recall&rev=10](https://help.ubuntu.com/community/PAE/PentiumM?action=recall&rev=10)


I think this page gives a better description and understanding of PAE and how the PAE flag is managed. It may appeal to 'more than average linux users'.
> 

Which is more helpful for a beginner?
Easy to understand?
Complete? 

- and other criteria you find relevant.

Maybe both versions can co-exist below a brief introductory page.

-o-

By the way, I published another instruction for Lubuntu 14.04 LTS and Pentium M or Celeron M processors at the following link (it is only a cook-book, not much is explained)

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

---

### Post by ibjsb4 on 2015-02-02
I think that for beginners, the command line needs to be avoided as much as possible.

Maybe have an 'Advance User' section.

---

### Post by mörgæs on 2015-02-02
Moving to *New to Ubuntu* for the time being, trying to get newcomers' opinion.

---

### Post by DoctorKokandy on 2015-02-03
The first and the last seem most helpful. The first explains it in a clear way that an even somewhat non-technical user can understand, except for the end - I don't know if most non-technical users would know what specific chipset (and codename) they run, though. That's a bit of specialized knowledge I think.) The last link there shows you how to find out whether your computer uses PAE. I would add that back at least.

---

### Post by grahammechanical on 2015-02-03
How do we get to that purple screen shown in the first and third links? I do actually know how to but there was a time when I did not know.

Notice how it is explained in this link under the heading Ubuntu CD Advanced Welcome page options.

> [COLOR=#333333][FONT=Ubuntu]As the CD boots, the user can gain access to the advanced page and its options by pressing any key when the small logo appears at the bottom of your screen:[/FONT][/COLOR]

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

In the first link, this does not match the options shown in the image

> [COLOR=#333333][FONT=Ubuntu]At the boot menu screen the options are[/FONT][/COLOR]

[LIST]
[*=left]Install
[*=left]Command-line options
[*=left]Advanced options
[*=left]Help
[/LIST]
[COLOR=#333333][FONT=Ubuntu]With the cursor on the top choice press F6.[/FONT][/COLOR] 



The image gives these options

> Try Ubuntu without installing
Install Ubuntu
Check disc for defects
Test memory
Boot from first hard disk


So, the instructions do not match what the new user sees on the screen. And then there is this in the first link

> [COLOR=#333333][FONT=Ubuntu]Technical note: After booting, "dmesg | grep -i pae" will now show "PAE forced!". You can use this as a check.[/FONT][/COLOR]

And this in the third link

> [COLOR=#333333][FONT=Ubuntu]After booting, [/FONT][/COLOR] dmesg | grep -i pae [COLOR=#333333][FONT=Ubuntu] will now show "PAE forced!". You can use this as a check.[/FONT][/COLOR]

Just how am I supposed to do that check? Am I to expect some words to appear on the screen as buntu is loaded? You expect me to know that it is a command and how to open the terminal. I do not even know what key produces this | character. :)

Remember, we are discussing this from the point of view of a person who is using an older computer and has been running a Windows OS for many years. And now wants to prolong the life of the machine now that Microsoft has finally stopped supporting that OS. And we want to help them do that without making it seem that Linux is too complicated to use.

As for the second link, what does "do not announce it by default" mean?

> [COLOR=#333333][FONT=Ubuntu]Many Pentium M processors have PAE support, but do not announce it by default. [/FONT][/COLOR]

> [COLOR=#252525][FONT=sans-serif]The Banias family processors [Also Known As - Pentium M] internally support PAE but do not show the PAE support flag in their CPUID information; this causes some operating systems (primarily Linux distributions) to refuse to boot on such processors since PAE support is required in their kernels[/FONT][/COLOR]

[http://en.wikipedia.org/wiki/Pentium_M](http://en.wikipedia.org/wiki/Pentium_M)

And that is the reason why we need to force PAE. Is it not true?

Regards.

---

### Post by ericbradshaw on 2015-02-04
The present version [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE) is most helpful for a beginner - in the beginning. It has a good headline, synopsis, eye-catching picture and the beginner can take away only what is needed. I think the next two [https://help.ubuntu.com/community/PA...=recall&rev=43]("https://help.ubuntu.com/community/PAE?action=recall&rev=43") and [https://help.ubuntu.com/community/PA...=recall&rev=10]("https://help.ubuntu.com/community/PAE/PentiumM?action=recall&rev=10") (and more information mentioned in other replies) are helpful, relevant and make the whole thing more complete. These should be included under "Details" along with another screenshot or two - maybe showing the Lubuntu and Xubuntu splash screens. Much like a newspaper article, everything that's really "needed" can be gleened from the first paragraph. But, if you keep reading; you get the full story.

---

### Post by Elfy on 2015-02-05
The current page has a lot of discussion which is not really needed on a technical help page.

---

### Post by Elfy on 2015-02-05
*Thread moved to **Documentation and Community Wiki Discussions**.*

---

### Post by Elfy on 2015-03-28
why is this wiki page about lubuntu? 

if there's a need for a lubuntu pae page then it should be at

[https://help.ubuntu.com/community/PAE/Lubuntu](https://help.ubuntu.com/community/PAE/Lubuntu)

---

### Post by sudodus on 2015-03-29
Hi Elfy,

Do you mean in the second headline and the Summary?

'A guide for getting computers with older Pentium M and Celeron M processors to work with the latest Lubuntu'

The picture is of Ubuntu, and Xubuntu plus a few other distros are also mentioned near the end of the page.

I think we can edit the current page [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE) to make you happy without making the text too clumsy.

I suggest that we start by stating:

'Computers that have issues with PAE are very old, so they need a medium light desktop environment, for example Xubuntu, or an ultra light desktop environment, for example Lubuntu.'

Then we can change Lubuntu to *ubuntu or mention both flavours (Lubuntu --> Lubuntu or Xubuntu)

---

### Post by Elfy on 2015-03-29
How about just making the page about PAE.

---

### Post by sudodus on 2015-03-29
It is a help page, so trying to help people solve their problem. A pure PAE page can be very brief and elegant, but may not help people, particularly beginners.

---

### Post by Elfy on 2015-03-29
yes, of course it is, currently it's a Lubuntu help page. Make it agnostic :)

---

### Post by mörgæs on 2015-03-29
My main focus here in Ubuntuforums is helping people with old gear. The most common problem I encounter is people trying to install Ubuntu on hardware which is not capable, and hence the most common advice given is 'Use a lighter distro like Lubuntu'. 

A computer with a Banias processor and the corresponding low-performance graphics chip is not suitable for Ubuntu. I would hate to be the one giving people the impression that Ubuntu is a viable option, it would not be genuine help. Even for stronger hardware I still recommend Lubuntu. With this hardware it's not possible to be agnostic, but some select, viable alternative distros are mentioned in the text.

---

### Post by mörgæs on 2015-03-29
@grahammechanical:

Thanks for your review. I shall take a look at the boot menu(s) again and see if anything does not fit.

About the *dmesg | grep -i pae* command: You are probably right that not everyone knows what it's about. On the other hand, it's not necessary for the install so if people skip this there is no harm done. 

I agree with you (and ibjsb4) that command line instructions should be kept to a minimum or reserved for an 'advanced users' page. We tend to forget how it was to be a beginner.

---

