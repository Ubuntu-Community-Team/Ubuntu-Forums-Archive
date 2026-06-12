---
title: "Nautilus, Preview and new image file formats?"
date: 2007-07-28
forum: Desktop Environments
---

### Post by AlwaysLearning on 2007-07-28
Hi all,

I use a Canon EOS 400D and the nature of the work I do with it requires that I record pictures in its highest-quality RAW mode (which outputs to 60MB-plus .CR2 files). I'd like to be able to get the file preview in Nautilus to work with these files but I haven't been able to find anything that tells me how to add new file formats yet (and yes, Nautilus preferences are set to show previews for image files up to 100MB, it just doesn't understand .CR2 files).

Using Dave Coffin's dcraw utility I can painlessly extract the JPEG encoded "thumbnails" from the CR2 files (I say thumbnails, even though they're 1936x1288 ) using the following command line for a specific image:
```
dcraw -c -e -o 1 img_0536.CR2 > img_0536.thumb.jpg
```
or in a Nautilus batch script:
```
#!/bin/sh
(while [ $# -gt 0 ]; do
	dcraw -c -e -o 1 "$1" > `basename "$1" CR2`thumb.jpg
	echo $1
	shift
	done
) | zenity --progress --auto-close --auto-kill --pulsate --text "Extracting thumbnails from RAW files..."
```
The next step is getting Nautilus to extract the thumbnails on-the-fly for display as image previews on the files. Can anyone help me out here?

Thanks in advance,
AlwaysLearning.

---

