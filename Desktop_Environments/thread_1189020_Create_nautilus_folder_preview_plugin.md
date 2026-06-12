---
title: "Create nautilus folder preview plugin"
date: 2009-06-16
forum: Desktop Environments
---

### Post by tirithen on 2009-06-16
Many with me would like to be able see a selection of the images a folder contains ontop of the folder icon. When having a large image collection with folders named after date and images inside them it's impossible to know in which folder to look without having a preview on the folder icon. M$ has supported this since XP so I think it's about time it got implemented into Ubuntu.

1. In a standard Ubuntu installation there are thumbnail images generated, they are stored in /home/user/.thumbnails with filenames like 0a5ad1bf2e16c722b06c4954bc47e2e5.png.

Somewhere there has got to be an registry of which thumbnail that belongs to which image.

2. It is possible to change the icon on individual folders

3. Make a script that:

[LIST=1]
[*]Checks if the content has changed since last view and if so:
[*]Combines a number of thumbnails from the images inside a folder into one icon image
[*]Saves the image into a registry/archive (could be like /home/user/.foldericons/root/home/user/images/album/folder.png)
[*]Applies the image as icon for that folder.
[/LIST]

Would this way be an ok method, surely there might be faster or more optimized ways of doing it but I would not mind if it's a bit slow and non standard as long as it's working.

So now the big questions, how would I do to make this work? Should I create some kind of plugin for nautilus? Where can I find out which thumbnail file belongs to which thumbail? How do I create a nautilus plugin?

Any thoughts are more than welcome! :-)

---

