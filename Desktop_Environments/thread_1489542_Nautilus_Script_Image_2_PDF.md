---
title: "Nautilus Script: Image 2 PDF?"
date: 2010-05-21
forum: Desktop Environments
---

### Post by jubantu on 2010-05-21
Hi,

I'm looking for a script to convert multiple images into a single PDF file. That is, I have several PNGs on my Desktop and I'd like to select all of them and create a PDF file via right mouse click. Does anyone know where I can find such a script?

Thanks in advance.

---

### Post by ad_267 on 2010-05-21
Install the imagemagick package then save a file containing this to ~/.gnome2/nautilus-scripts/CreatePDF

```
#!/bin/bash

convert $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS Output.pdf
```

Right click on that file and go to its properties and make it executable.

Now you can create a PDF from the scripts menu.

---

### Post by fermulator on 2011-04-23
How to control the order of the pages though?

I have 2x PNG files, and they're "foo.png" and "bar.png".  I select foo, and then CTRL+click on bar, and bar always is the first page, but I want foo to be the first page.

I also tried doing .. myImage1.png, and myImage2.png (thinking alpha sorting..) but still the last page comes first...

---

### Post by kaibob on 2011-04-24
On my computer, user-selected files are processed by a Nautilus script in the order that they are shown in the right pane of the Nautilus file browser. This order can, of course, be changed by clicking on "Name" or "Size" or one of the other headers. The order in which the files are selected by the user appears to have no impact. 

If there is no other alternative, one option is to have the Nautilus script prompt the user for the desired sort order. The following is an example. This script is a bit cumbersome--perhaps another forum member will have a simpler solution.  

This script uses a zenity dialog, which I don't believe is installed by default. It's  in the repo's and is small is size.

```
#!/bin/bash

files=("$@")

pages=$(zenity --entry --title "File order" --text "Enter space-separated numbers")

for page in ${pages} ; do
  newfiles+=("${files[page-1]}")
done

convert "${newfiles[@]}" output.pdf
```

---

### Post by samuelcersosimo on 2013-02-21
> **ad_267 said:**
> Install the imagemagick package then save a file containing this to ~/.gnome2/nautilus-scripts/CreatePDF

```
#!/bin/bash

convert $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS Output.pdf
```Right click on that file and go to its properties and make it executable.

Now you can create a PDF from the scripts menu.

What would that script look like if I wanted that each selected file became an individual PDF? Like a batch comand.

Thanks for the tip. Very good.

---

### Post by oldos2er on 2013-02-22
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

