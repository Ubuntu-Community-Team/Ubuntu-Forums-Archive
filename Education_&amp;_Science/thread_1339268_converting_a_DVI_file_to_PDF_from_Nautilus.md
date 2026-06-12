---
title: "converting a DVI file to PDF from Nautilus"
date: 2009-11-27
forum: Education &amp; Science
---

### Post by perroazul on 2009-11-27
I wrote a small script for converting dvi files to pdf (assuming that your latex document includes eps figures, which means that you can't run pdflatex directly):
```

#!/bin/bash
ind=`expr index "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" .`
filename=${NAUTILUS_SCRIPT_SELECTED_FILE_PATHS:0:$ind-1}
(echo 0;dvips -P pdf $filename.dvi;sleep 1;echo 50;
ps2pdf $filename.ps;rm $filename.ps;echo 100)| zenity --progress --title="Dvi 2 PDF... " --text="converting dvi file to pdf" --pulsate

```

save this script to ~/.gnome2/nautilus-scripts/ then you just have to select a file, do right click, and run the script. This might be useful to somebody ;)
cheers

---

