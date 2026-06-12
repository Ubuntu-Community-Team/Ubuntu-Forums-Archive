---
title: "Scientific Program -- help finding or installing"
date: 2009-04-14
forum: General Help
---

### Post by Norrit on 2009-04-14
Hi, I'm having an interesting little problem here.

So I work with a lab at a major university doing Rutherford Backscattering Spectroscopy, our data is gathered and then stored in a .RBS (RUMP) file format on the mainframe for our group. The process we use in windows is that we have to take this .RBS file and convert it to an .AS1 file type using the program "Specon". This allows us to then take this data, open it with a simple notepad program, or import it directly into a spreadsheet for analysis.

The program we use in the windows boxes does not install on wine at all, I believe the program was written in VB and from what I hear you cannot get VB to run on linux. Please if I'm wrong here tell me. I installed the program fine and when I run it I get the following error:

"Run-time error '429':
Activex component can't create object."

This error is not such a big deal if someone can suggest another process of converting these files. So they are stored as "*.RBS" files which when you use the:

file ./*.RBS

command it returns ./*.RBS: data. So I'm not sure if I can just convert the file from data to ascii, cause I believe that's all that this program does, and if so, how do I go about doing this?

Links --
[http://www.hongserver.com/Specon/Specon.html](http://www.hongserver.com/Specon/Specon.html)
[http://www.genplot.com/doc/RUMP/rbs_inf.htm](http://www.genplot.com/doc/RUMP/rbs_inf.htm)

---

### Post by codeseer on 2009-04-14
> **Norrit said:**
> Hi, I'm having an interesting little problem here.

So I work with a lab at a major university doing Rutherford Backscattering Spectroscopy, our data is gathered and then stored in a .RBS (RUMP) file format on the mainframe for our group. The process we use in windows is that we have to take this .RBS file and convert it to an .AS1 file type using the program "Specon". This allows us to then take this data, open it with a simple notepad program, or import it directly into a spreadsheet for analysis.

The program we use in the windows boxes does not install on wine at all, I believe the program was written in VB and from what I hear you cannot get VB to run on linux. Please if I'm wrong here tell me. I installed the program fine and when I run it I get the following error:

"Run-time error '429':
Activex component can't create object."

This error is not such a big deal if someone can suggest another process of converting these files. So they are stored as "*.RBS" files which when you use the:

file ./*.RBS

command it returns ./*.RBS: data. So I'm not sure if I can just convert the file from data to ascii, cause I believe that's all that this program does, and if so, how do I go about doing this?

Links --
[http://www.hongserver.com/Specon/Specon.html](http://www.hongserver.com/Specon/Specon.html)
[http://www.genplot.com/doc/RUMP/rbs_inf.htm](http://www.genplot.com/doc/RUMP/rbs_inf.htm)

Obtain [Winetricks]("http://wiki.winehq.org/winetricks") and run:

```

sh ./winetricks wsh56

```

Then try again.

---

### Post by 3Miro on 2009-04-14
You can also try Virtual Box to install Windows under Linux. Data conversion programs will run (since you do not need graphics) and they will run about as fast as if let alone.

If you know the exact format of .RBS files, then you can write your own program for conversion (I am assuming that the program that you are using supports many formats, it shouldn't be too hard to do a simple program for just one format).

---

### Post by Norrit on 2009-04-14
codeseer - Thanks so much, I had seen information about that previously on other websites in my extensive web searching haha. And had tried it but it didnt cooperate for some reason previously. Now it's working perfectly fine! Thanks a lot.

3Miro - Yeah that's what I was thinking about doing, but I couldn't find the APIs for the C or Fortran libraries used for RUMP. Luckily it finally decided to start working in Wine, thanks though.

---

