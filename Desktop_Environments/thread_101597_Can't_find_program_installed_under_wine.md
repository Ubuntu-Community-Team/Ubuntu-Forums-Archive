---
title: "Can't find program installed under wine"
date: 2005-12-10
forum: Desktop Environments
---

### Post by GabrielWolff on 2005-12-10
I had a problem like that before, but not as...

I just installed a program with wine, and now I can't find it, not under Applications, not with the search option, and not by typing the programs name into the command line or with the console.

What happened?

Gabriel

---

### Post by manicka on 2005-12-10
What program did you install?

---

### Post by GabrielWolff on 2005-12-10
ENCORE, it's a notation program (music notes, ya'anee)

For musicians Linux sucks (as far as I'm able to see it), so I'm trying to install win programs that I remember working fine for me

But what does it matter? Where can a program be installed? And how is decided if it later on appears under Applications?

Gabriel

---

### Post by @jens on 2005-12-10
[QUOTE=GabrielWolff]I had a problem like that before, but not as...

I just installed a program with wine, and now I can't find it, not under Applications, not with the search option, and not by typing the programs name into the command line or with the console.

Somewhere in /home/user/.wine/fake-windows? Just a shot.

cheers
Jens

---

### Post by greenpenguin on 2005-12-10
Its under ~/.wine/something/c_drive/ or similar (not on ubuntu at the second to i cant check).
 
Have you tried out roseguarden/audacity/sweep?  I've found them to be better than any of the windows one i can get my hands on.

---

### Post by GabrielWolff on 2005-12-10
[QUOTE=greenpenguin]Its under ~/.wine/something/c_drive/ or similar (not on ubuntu at the second to i cant check).
 
Have you tried out roseguarden/audacity/sweep?  I've found them to be better than any of the windows one i can get my hands on.[/QUOTE]

Yeah, thanx for that. I found the encore.exe, now what do I do with it? I obviously can't open it as program under ubuntu, as it, well, an .exe...

I have tried both rosegarden and audacity, but it's different programs than what I am looking for. I compose, and want to write the music down. uUnder win that's done with Finale or Sibelius or similar programs, but lilypond, the Linux notation program, is hard. Thanx, though

Gabriel

---

### Post by Rackerz on 2005-12-10
Ok, right click that file and in the menu that comes up after right clicking there should something with says 'Open With ..' or similar. Choose Wine.

---

### Post by Hairy_Palms on 2005-12-10
Sibelius is one program i would love to have under linux :( i never got it working under wine either :(

---

### Post by Rackerz on 2005-12-10
Did you try to use Crossover Office?

---

### Post by SickTwist on 2005-12-10
[QUOTE=GabrielWolff]ENCORE, it's a notation program (music notes, ya'anee)

For musicians Linux sucks (as far as I'm able to see it), so I'm trying to install win programs that I remember working fine for me . . .[/QUOTE]

I'm not sure if you have seen these but I thought that I would mention them:

[LIST]
[*][Lilypond]("http://www.lilypond.org/doc/v1.6/Documentation/out-www/index.html")
[*][Gscore]("http://www.gscore.org/")
[*][abc]("http://staffweb.cms.gre.ac.uk/~c.walshaw/abc/")
[*][abc plus]("http://abcplus.sourceforge.net/")
[*][Philip's Music Writer]("http://www.quercite.com/pmw.html")
[/LIST]

---

### Post by GabrielWolff on 2005-12-10
[QUOTE=Rackerz]Ok, right click that file and in the menu that comes up after right clicking there should something with says 'Open With ..' or similar. Choose Wine.[/QUOTE]

Did that
Worked
Froze
Won't open again.

Is that Wine telling me it didn't install encore properly and I should forget about it, or is it wine, telling me to restart, or try again?

Gabriel

---

### Post by GabrielWolff on 2005-12-10
[QUOTE=Rackerz]Did you try to use Crossover Office?[/QUOTE]

Did that
Installed alright, or at least seems so.
And now? I tried to do it the same way like with wine (right click => open with crossover), but it gave me the installation screen once againn.

How do I do it?

Thanx

Gabriel

---

### Post by Rackerz on 2005-12-10
Crossover Office should have created it's own menu in the applications menu. It should also have created a menu similar to 'Windows applications' or 'Crossover Office Applications'. What you installed should be in there.

---

### Post by GabrielWolff on 2005-12-10
[QUOTE=Rackerz]Crossover Office should have created it's own menu in the applications menu. It should also have created a menu similar to 'Windows applications' or 'Crossover Office Applications'. What you installed should be in there.[/QUOTE]

Nothing. Under Applications I got CrossOver, and then:
1) Office Documentation
2) Office Setup
3) Reset CrossOver Office
4) Simulate Windows Reboot
5) Uninstall Office

I have other programs installed under CrossOver, but nothing's there.
How come?

Gabriel

---

