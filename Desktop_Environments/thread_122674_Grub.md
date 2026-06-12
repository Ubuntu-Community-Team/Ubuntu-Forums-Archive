---
title: "Grub"
date: 2006-01-28
forum: Desktop Environments
---

### Post by ESPOiG on 2006-01-28
how do i add a pic to the background of my grub bootloader, what do i need and what config file do i have to edit to do it 

thx alot

---

### Post by GTvulse on 2006-01-28
Open your desired splash image in The Gimp. Reduce its size to 640x480 and reduce its colors to 15 indexed colors. Save as an XPM. Compress with gzip. Now copy to the boot directory:
```
sudo cp my_cool_grub_splash.xpm.gz /boot/grub/splash.xpm.gz
```
After this you are ready to update your grub menu:
```
sudo update-grub
```
That's it.

---

### Post by ESPOiG on 2006-01-28
really... well that is pretty damm simple thx alot ill try it later

---

### Post by GTvulse on 2006-01-28
I think you could use up to 18 indexed colors, but my memory doesn't help me on that one. 15 hasn't failed me yet. ;-)

---

### Post by GTvulse on 2006-01-28
[QUOTE=dradul]I think you could use up to 18 indexed colors, but my memory doesn't help me on that one. 15 hasn't failed me yet. ;-)[/QUOTE]
This is serendipity in action. I just found this in my mail: [http://www.freesoftwaremagazine.com/free_issues/issue_10/grub_intro/index_p3.html](http://www.freesoftwaremagazine.com/free_issues/issue_10/grub_intro/index_p3.html). The maximum is [b]14[/] indexed colors not 15 as I recalled.

---

### Post by ESPOiG on 2006-01-29
yeh i tried 14 wen 15 didnt work... but im not sure now as how im supposed to be doin these pics

i start with a blank 640x480 @ 14 pixles per inch or wateva
transperant background 
then i just copy and paste a pic
then i save as xpm.gz it says export i do that

then i copy into the grub folder as splash and then i run update

once i reboot it just gives me a fukd pic instead of wat i made it is all big... liney... distorted ... weird colors  etc etc

so i dunno if i did sumtin rong along the way if i did plz tell me

---

### Post by GTvulse on 2006-01-29
No, no. That's not the way to do it. Keep it simple: ;-) 

[list=1]
[*] Open image with The Gimp.
[*] Scale image size. (Do a cubic interpolation for best results).
[*] Reduce to 14 indexed colors. (Try different dithering modes to find what works best, undo is your friend). 
[*] Save resulting image in XPM format.
[*] Compress xpm file with gzip. OK, ok, that can be a hurdle; two easy methods come to my mind:
[list=a]
[*] In a terminal window ```
~$ gzip -9N your_xpm_file.xpm
``` The resulting file name will be [font=monospace]your_xpm_file.xpm.gz[/font] 
[*] Look for the resulting xpm file in nautilus or konqueror, right-click once, activate the archiver and compress. Using gnome-archiver, just add ".gz" at the end of the file and click OK. With KArchiver, it is more complex but similar.
[/list]
[*] Copy [font=monospace]your_xpm_file.xpm.gz[/font] to [font=monospace]/boot/grub/splash.xpm.gz[/font].
[/list]

---

### Post by ESPOiG on 2006-01-29
k wat i really wantd to know is the change of pixles the (pixles per inch) thingo cuz that is wat i been doing and it didnt work at first 

im tryin now but this is basically wat i did the first time as well

---

### Post by Haegin on 2006-01-29
What do you do if you have /boot on a seperate partition? I have a raid setup with 2 sata drives and grub doesn't like raid so I have a seperate partition on the first sata drive (/dev/sda1) for /boot. When I was reading the grub page in the wiki it mentioned problems with having /boot on a sperate partition but it didn't say how that affects splash images. Also how do I find what my (hdx,y) thing is for the boot device (x and y are two different numbers)?

Thanks in advance

---

### Post by GTvulse on 2006-01-29
[QUOTE=ESPOiG]k wat i really wantd to know is the change of pixles the (pixles per inch) thingo cuz that is wat i been doing and it didnt work at first 

im tryin now but this is basically wat i did the first time as well[/QUOTE]
No, changing the pixels per inch won't work; 72 dpi is what you'll get and that's already hi-res. You are using the EGA buffer emulation in the BIOS of your mainboard, not even the lowest quality emulation of whatever expensive video card you may have in there. Think 1990. Back then you would have paid US$5000 just for the privilege of 4-bit color in your PC...

---

### Post by GTvulse on 2006-01-29
[QUOTE=Human Prototype]What do you do if you have /boot on a seperate partition? I have a raid setup with 2 sata drives and grub doesn't like raid so I have a seperate partition on the first sata drive (/dev/sda1) for /boot. When I was reading the grub page in the wiki it mentioned problems with having /boot on a sperate partition but it didn't say how that affects splash images. Also how do I find what my (hdx,y) thing is for the boot device (x and y are two different numbers)?

Thanks in advance[/QUOTE]
Having /boot in a different partition has nothing to do with adding a grub splash image, particularly if use update-grub (as prescribed by the Debian Way(tm) ;-)).

---

### Post by ESPOiG on 2006-01-29
no its all fine i have my pic in the correct place and i have grub detecting it... it is just now how do i get the splash.xpm to 14 bit cuz if it aint the pixels per inch i dunno how

were in gimp can u do this

---

### Post by Haegin on 2006-01-30
Use Image>Mode>Indexed and set the number of colours to 14 or lower then save as a .xpm.gz (gimp can do the compression as well)

---

