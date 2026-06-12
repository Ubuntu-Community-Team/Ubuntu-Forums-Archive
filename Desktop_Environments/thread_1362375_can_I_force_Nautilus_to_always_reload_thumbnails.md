---
title: "can I force Nautilus to always reload thumbnails?"
date: 2009-12-23
forum: Desktop Environments
---

### Post by rebeltaz on 2009-12-23
I have a directory where I download images from my digital camera, edit them, rename them and then move them to another directory. Then I will place the next batch of images in that directory to be processed. I have Nautilus set to icon view on that folder, but since the filenames coming off the camera are always the same, the thumbnails get confused. I know I can delete .thumbnails, and that does work, but it is time consuming and repetitive to do that every time and besides that, it also removes thumbnails that do stay the same. Is there any way that I can force just that directory to always reload the thumbnails? 

I guess if nothing else, I could add a cron job to run at startup that would delete the .thumbnails file, but that goes back to deleting wanted thumbnails as well.

thanks...

---

### Post by pixolex on 2010-01-11
Hit View->Refresh or Ctrl+R or F5 

That reloads every thing.

---

### Post by rebeltaz on 2010-01-11
> **pixolex said:**
> Hit View->Refresh or Ctrl+R or F5 

That reloads every thing.

Yeah, but what I would really like is for the system to refresh the thumbnails itself each time I access that directory.

Thank you, though.

---

### Post by wishingstar on 2010-05-25
Hey

Nautilus does not have a GUI method to reload thumbnails, you have to use the terminal:

Try running:

```
rm -rf ~/.thumbnails
killall nautilus && nautilus

```

This code will delete the thumbnails folder in nautilus and force to restart and regenerate the thumbs, i'm afraid so far i haven't found a way to refresh thumbs on individual basis.

Hope this helps.

---

### Post by Barafu Albino Cheetah on 2010-05-25
Create an empty .thumbnail file in the target directory and restrict acces to it. Worked several yaers ago, didn't try now.

---

