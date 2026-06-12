---
title: "Text to Speech Software"
date: 2005-04-23
forum: Desktop Environments
---

### Post by Amdmhz on 2005-04-23
Hi all. My 8 year old son can not talk. I want to setup a laptop with Ubuntu on it that has text to speech capabilites so that we can hear the words he types. Does anyone know of linux software that will do this? Something that will work great in Ubuntu.

Thanks for your help

---

### Post by nad on 2005-04-23
Please see:

[http://linux-sound.org/speech.html](http://linux-sound.org/speech.html)

I know that there are debian packages that use the festival-synthe engine, but I do not know if there are any packages for ubuntu. Perhaps someone else will chime in or make a search through your synaptic package manager.

Dan M

---

### Post by heimo on 2005-04-23
I have experimented using festival, which is a speech synthesizer engine, but what you are searching for is probably a front end to festival of flite. I haven't used those, but I did a little search on this subject and here are the descriptions of those packages (first the two engines I mentioned). I don't know how useful or suitable those programs are, but I include all the programs I thought could be of interest.

festival
> Description: general multi-lingual speech synthesis system
 Festival offers a full text to speech system with various APIs, as
 well an environment for development and research of speech synthesis
 techniques. It includes a Scheme-based command interpreter.
 .
 Besides research into speech synthesis, festival is useful as a
 stand-alone speech synthesis program. It is capable of producing
 clearly understandable speech from text.
 

flite
 > Description: A small run-time speech synthesis engine
 Flite is a small fast run-time speech synthesis engine.  It is the
 latest addition to the suite of free software synthesis tools
 including University of Edinburgh's Festival Speech Synthesis System
 and Carnegie Mellon University's FestVox project, tools, scripts and
 documentation for building synthetic voices.  However, flite itself
 does not require either of these systems to run.
 


kmouth
 > Description: A type-and-say KDE front end for speech synthesizers
 A type-and-say KDE front end for speech synthesizers.
 It includes a history of spoken sentences from which the user can select
 sentences to be re-spoken.
 This package is part of KDE, as a component of the KDE accessibility module.
 See the 'kde' and 'kdeaccessibility' packages for more information.
 

screader
  > Description: Screen reader using software or hardware speech synthesizer
 The background program screader reads the screen and puts the information
 through to a software Text-To-Speech package (Like `festival') or a
 hardware speech synthesizer.
 


emacspeak
 > Description: speech output interface to Emacs
 Emacspeak is a speech output system that will allow someone who
 cannot see to work directly on a UNIX system.  Emacspeak is built on
 top of Emacs.  Once you start emacs with emacspeak loaded, you get
 spoken feedback for everything you do.  Your mileage will vary
 depending on how well you can use Emacs.  There is nothing that you
 cannot do inside Emacs :-).  This package includes speech servers
 written in tcl to support the DECtalk Express and DECtalk MultiVoice
 speech synthesizers.  For other synthesizers, look for separate
 speech server packages such as emacspeak-ss.
 

recite
  > Description: English text speech synthesizer
 Recite is a program to do speech synthesis.  The quality of sound
 produced is not terribly good, but it should be adequate for reporting
 the occasional error message verbally.


---

### Post by Amdmhz on 2005-04-25
Thanks for the suggests, I will try them out. Thanks again :)

---

### Post by heimo on 2005-04-25
[QUOTE=Amdmhz]Thanks for the suggests, I will try them out. Thanks again [/QUOTE]
I tried to install and use some of those. I didn't use much time, but it seemed like some required hardware synthesizer, some kde-programs crashed on my Gnome desktop and the one that worked had a very disappointing audio quality.

I'll do some more searching and testing later on.

---

### Post by c_dog on 2005-04-25
[QUOTE=Amdmhz]Hi all. My 8 year old son can not talk. I want to setup a laptop with Ubuntu on it that has text to speech capabilites so that we can hear the words he types. Does anyone know of linux software that will do this? Something that will work great in Ubuntu.

Thanks for your help[/QUOTE]

I've played with KSayIt a bit. It runs as a frontend for kttsmgr (K Text to Speech Manager). They work in Gnome also. You can find them in the Ubuntu Universe repositories. If you don't have special speech to text hardware, KSayIt does a fair job running on a normal PC sound card with Festival. Festival is a software speech synthesizer engine. Festival seems to be the easiest open source speech engine to get to work. You can configure KSayit to either "play back" chunk of text copied to the clipboard or text entered into kttsmgr's text box. I've thought about using KSayIt to make audiobook Podcasts of Gutenburg Project text or maybe Slashdot headlines for the road.

---

### Post by heimo on 2005-04-25
Ok! I'm back with my suggestions... :) Yeah - festival is probably nice backend for this purpose. Another engine could be kttsd. What I did... Was install KDE (kubuntu-desktop), install festival, install kmouth and in settings->configure Kmouth I put General Options -> Command for speaking texts '/usr/bin/festival --tts' and I have a program with predefined texts(* and history of previous texts - everything coming out with quite good software speech synthesis.

Oh, I actually did install ksayit and kttsd too. Without the backend installed ksayit just crashed. I guess it's a package dependency bug - frontend should probably depend on some "speech synthesizer backend" package.

So the conclusion from me is that check kmouth and ksayit, install festival and kttsd. These work at least on KDE (kubuntu-desktop). I actually had to do a fresh install on my computer today (not related to this) and I installed using Ubuntu 5.04 CD, but installed kubuntu-dekstop after the installation was ready.

You can try if it works on Gnome (the default desktop environment on Ubuntu). If you encounter any problems, please do not hesitate to ask.


*) EDIT: Of course not only predefined - but also what ever you type yourself.

Wow! It has TAB completion with dictionary. This thing is neat! Very, very fast to type something as it suggests words from dictionary and when you see correct one, just hit tabulator and you don't have to type rest of that word. This is nice.

---

