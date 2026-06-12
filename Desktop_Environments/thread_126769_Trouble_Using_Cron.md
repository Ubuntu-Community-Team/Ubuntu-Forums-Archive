---
title: "Trouble Using Cron"
date: 2006-02-07
forum: Desktop Environments
---

### Post by kenquad on 2006-02-07
Hi all:

I'm having trouble using Kcron.  It doesn't appear to do anything.  What I want to do is schedule a certain shell script to run in the middle of the night so as not to disrupt the network, but as of now I can't get anything on Cron to work.

To test, I opened Kcron and scheduled GIMP to run today at a certain time.  The appointed time came and went with nothing; I even ran top to see if it was in the background.  What could I be doing wrong?

Thanks

---

### Post by GeneralZod on 2006-02-07
GUI apps don't work easily with cron, as they don't know the DISPLAY setting.  Do

```

echo $DISPLAY

```

and take note of the value.  Then in your gimp start up script, you will need *something* like 

```

export DISPLAY=**That value here**; gimp

```

or some such.  Experiment by trying to open gimp one minute into the future.  I can't remember offhand what the executable name for gimp is (gimp? gimp2? I forget :)) so you'll have to make sure that's right, to.

---

### Post by kenquad on 2006-02-07
Good to know; thanks.  But the problem worked itself out easily; I just created an item wiht my command text (a wget thing) rather than calling the shell script.  Actually, it might have been working all along for all I know.  Thanks!

---

