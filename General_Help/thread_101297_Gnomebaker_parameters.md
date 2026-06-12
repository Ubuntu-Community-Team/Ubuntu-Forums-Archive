---
title: "Gnomebaker parameters"
date: 2005-12-09
forum: General Help
---

### Post by ercork on 2005-12-09
I'm fairly new to Linux. I've been trying Mepis and PCLOS for a few months and have now moved on to Ubuntu. On the whole, I think it's great except for this one cd burning problem that I have.
Is there any way to send parameters to cdrecord through Gnomebaker? I'm using a Teac CD-W28E drive on an IBM Thinkpad T22 and whenever I try to burn, I get the message from cdrecoord saying I'm using a high-speed medium on a low speed drive and it won't allow me to continue. I've used the same drive-disc combination on Windows using several different programs without any problems. I've also used K3b when I was on Mepis and it worked fine, but only when I entered the -force parameter in the cdrecord options of K3b. I'd rather stick with Gnomebaker than download 100Mb worth of K3b so if somebody knows how to do this I'd really appreciate it. I'm fairly certain that the problem is as simple as adding this parameter because from a terminal I tried: 
cdrecord -force blank=all 
and it erased my cdrw perfectly.

Thanks in advance.

---

### Post by ercork on 2005-12-14
I posted thes same question on the gnomebaker support forum and two potential solutions were proposed:

1. Use a shell script to do the work (ie replace the cdrecord command with your own bash wrapper around it which will just add the -force switch). This would require some bash skills 
2. Find where Gnomebaker calls cdrecord and append the -force switch (some knowledge of the GB source needed).

Unfortunately, I don't really have either of the skills mentioned. As far as I can see, no. 1 looks more straightfoward so if somebody could show how to write such a script it would be a big help.
Thanks again

---

### Post by quonsar on 2005-12-14
i think number one would be easy. 

```
sudo mv /usr/bin/cdrecord /usr/bin/cdrecord-original
```

then create the wrapper:

```
sudo gedit /usr/bin/cdrecord
```

type in the following:

```

#!/bin/bash
/usr/bin/cdrecord-original -force

```

save the file. make it executable:

```
sudo chmod +x /usr/bin/cdrecord
```

now (if i've got all the syntax right) when gnomebaker calls cdrecord, it will be calling your wrapper instead, which simply calls the original cdrecord program with the -force parameter.

---

### Post by ercork on 2005-12-16
Thanks for the reply quonsar. I did what you suggested but no luck unfortunately. Gnomebaker now gives me a different error message:


cdrecord: No tracks specified. Need at least one.
Usage: cdrecord [options] track1...trackn

Use	cdrecord -help
to get a list of valid options.

Use	cdrecord blank=help
to get a list of valid blanking options.

Use	cdrecord dev=b,t,l driveropts=help -checkdrive
to get a list of drive specific options.

Use	cdrecord dev=help
to get a list of possible SCSI transport specifiers.



Maybe there should be a variable somewhere in the bash script?

---

### Post by quonsar on 2005-12-16
gah! of course! gnomebaker is calling it with a bunch of parameters. try this:

in the /usr/bin/cdrecord file:

```
#!/bin/bash
/usr/bin/cdrecord-original -force "$@"
```

i fooled around a bit with a test script and that SHOULD pass on the rest of the parameters. hope it helps!

---

### Post by ercork on 2005-12-16
Perfect - no more burning problems thanks to your little script. For anybody interested, I submitted a feature request on the Gnomebaker forum that future versions would allow you to enter those switches somewhere in the program interface.

Thanks again for the help quonsar.

---

### Post by gamehack on 2005-12-17
As I said on GB's forums, feature is implemented ;)
[http://www.flickr.com/photo_zoom.gne?id=74387002&size=o](http://www.flickr.com/photo_zoom.gne?id=74387002&size=o)

---

