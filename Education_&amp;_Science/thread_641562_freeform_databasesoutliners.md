---
title: "freeform databases/outliners"
date: 2007-12-15
forum: Education &amp; Science
---

### Post by myotis on 2007-12-15
What options are available on Linux for personal data management, for example when gathering data for research.

On Windows you have programs like Zoot, Ultrarecall and InfoSelect and on the Mac there is DevonThink. There are also simpler Outliner type programs that allow for data storage.

I've found Treeline which seems to fall into this category, but what do people use for gathering and collating research data.

Graham

---

### Post by countryparson on 2007-12-18
Notecase works well for me.  It's pretty basic/simple though.
I also have used KDissert for writing but not for storing information.
Both are in the "universe" repositories.

There are a few others I've seen but notecase fits what I need the best.

---

### Post by myotis on 2007-12-18
Scott,

This looks very interesting, especially, as it is cross platform.

I will certainly have a look at it.

Thanks,

Graham

---

### Post by Typhoon on 2007-12-19
I suppose it depends in part on the kind of information you are collecting. Mine is always in the form of text. I use Emacs + remember to collect notes as I am reading or from Web pages.

Remember collects each item as an outline object in a designated.

The Emacs outliner is quite powerful. I have mine setup to imitate all the functions of Thinktank (the first outliner I used extensively) including the "hoist" function.

Cheers,
Typhoon

---

### Post by myotis on 2007-12-20
Typhoon,

> **Typhoon said:**
> . I use Emacs + remember to collect notes as I am reading or from Web pages.

The Emacs outliner is quite powerful. I have mine setup to imitate all the functions of Thinktank (the first outliner I used extensively) including the "hoist" function.


I am currently  using Emacs+OrgMode+Remember on Windows and the Mac, and for time management/project management I will stay with this arrangement. But a lot of information I work with is images, where Emacs is less useful, nor does it offer the ease of hitting F1 in email and having a copy of the email archived in Eaglefiler (on the Mac). 

Having said that, in spite of asking this here to allow me to explore some of the alternatives, an all Emacs solution would be my preferred solution. 

I would be really interested to know how you have set Emacs up to work like ThinkTank (bear in mind that my knowledge of Emacs is still limited)

Thanks for the reply,

Graham

---

### Post by Typhoon on 2007-12-27
> **myotis said:**
> Typhoon,



I am currently  using Emacs+OrgMode+Remember on Windows and the Mac, and for time management/project management I will stay with this arrangement. But a lot of information I work with is images, where Emacs is less useful, nor does it offer the ease of hitting F1 in email and having a copy of the email archived in Eaglefiler (on the Mac). 

Having said that, in spite of asking this here to allow me to explore some of the alternatives, an all Emacs solution would be my preferred solution. 

I would be really interested to know how you have set Emacs up to work like ThinkTank (bear in mind that my knowledge of Emacs is still limited)

Thanks for the reply,

Graham

I don't know how to deal with images. All of my research/notetaking is text based.

Emacs/Thinktank: here is the setup for outline-minor-mode which I use when writing in LaTeX. It is set in the Customization buffers (I have split the lines to make it easier to read here. Foldout provides the foldout-zoom-subtree command which is the old Thinktank "Hoist".

 '(outline-minor-mode-hook 
(quote ((lambda nil (require (quote foldout))) 
(lambda nil (define-key outline-minor-mode-map [f10] (quote outline-cycle)) 
(define-key outline-minor-mode-map [C-kp-down] (quote outline-forward-same-level)) 
(define-key outline-minor-mode-map [C-kp-up] (quote outline-backward-same-level)) 
(define-key outline-minor-mode-map [C-kp-add] (quote show-entry)) 
(define-key outline-minor-mode-map [C-kp-subtract] (quote hide-entry)) 
(define-key outline-minor-mode-map [s-kp-subtract] (quote hide-subtree)) 
(define-key outline-minor-mode-map [s-kp-add] (quote show-children)) 
(define-key outline-minor-mode-map [s-kp-right] (quote outline-demote)) 
(define-key outline-minor-mode-map [s-kp-left] (quote outline-promote)) 
(define-key outline-minor-mode-map [s-kp-multiply] (quote show-subtree)) 
(define-key outline-minor-mode-map [s-up] (quote foldout-zoom-subtree)) 
(define-key outline-minor-mode-map [s-down] (quote foldout-exit-fold))))) t)

Cheers,
Typhoon

---

### Post by myotis on 2007-12-27
> **Typhoon said:**
> I don't know how to deal with images. All of my research/notetaking is text based.

Emacs/Thinktank: here is the setup for outline-minor-mode which I use when writing in LaTeX. It is set in the Customization buffers (I have split the lines to make it easier to read here. Foldout provides the foldout-zoom-subtree command which is the old Thinktank "Hoist".

 '(outline-minor-mode-hook 
(Typhoon

Thanks, I will give this a try :-)

Graham

---

