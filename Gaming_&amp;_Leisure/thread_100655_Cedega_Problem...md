---
title: "Cedega Problem.."
date: 2005-12-08
forum: Gaming &amp; Leisure
---

### Post by icemilo on 2005-12-08
Hello people^^

I have just installed my cedega... to run GTA or Warcraft3..

But i am getting this error
> fixme:wave:ALSA_WaveInit -fixme:wave:ALSA_WaveInit -
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
/usr/lib/cvscedega/bin/wine: can't exec 'war3.exe': error=21


> err:module:map_image Could not map section .text, file probably truncated
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
fixme:wave:ALSA_WaveInit -fixme:wave:ALSA_WaveInit -
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
/usr/lib/cvscedega/bin/wine: can't exec 'gta_sa.exe': error=21
fixme:xrender:X11DRV_XRender_Finalize Free cached glyphsets
root@icemilo:/mnt/windows/Program Files/Rockstar Games/GTA San Andreas# vi /root/.cvscedega/config
root@icemilo:/mnt/windows/Program Files/Rockstar Games/GTA San Andreas# cvscedega gta_sa.exe
err:module:map_image Could not map section .text, file probably truncated
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
Building font metrics. This may take some time...
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-normal--13-120-75-75-c-70-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-normal--13-120-75-75-c-80-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-normal--14-130-75-75-c-70-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-normal--15-140-75-75-c-90-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-normal--18-120-100-100-c-90-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-bold-r-semicondensed--13-120-75-75-c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-o-normal--13-120-75-75-c-70-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-o-normal--13-120-75-75-c-80-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-o-semicondensed--13-120-75-75-c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--6-60-75-75-c-40-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--7-70-75-75-c-50-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--8-80-75-75-c-50-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--9-90-75-75-c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--13-120-75-75-c-70-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--13-120-75-75-c-80-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--14-130-75-75-c-70-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--15-140-75-75-c-90-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--18-120-100-100-c-90-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-normal--20-200-75-75-c-100-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-semicondensed--12-110-75-75-c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
fixme:font:LFD_InitFontInfo font '-misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso8859-16' has unknown character encoding '16' in known registry 'iso8859'
Done building font metrics
fixme:wave:ALSA_WaveInit -fixme:wave:ALSA_WaveInit -
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
/usr/lib/cvscedega/bin/wine: can't exec 'gta_sa.exe': error=21


can any one tell me what i need to do ..? 

Thanks ^^

---

### Post by newuser111 on 2005-12-08
problem appears to be with alsa/your sound card

try this guide [http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

it sounds like you also need to install the truetype fonts package that comes with cedega

---

### Post by vyktor69 on 2006-01-05
I had a similar issue with WoW until I downloaded wow_wine-0.9.1 and followed the directions on [http://ubuntuforums.org/showthread.php?t=92367&page=16](http://ubuntuforums.org/showthread.php?t=92367&page=16)
Don't know if it'll help but it was the only way I could run WoW at above 15 fps after the 1.9 patch. 
I don't know if it would help in your case but you never know. :)

---

