---
title: "Picasa and Evolution -- Picasa cannot send photo via email"
date: 2009-02-10
forum: General Help
---

### Post by jyanek on 2009-02-10
Using Picasa 3.0.0 and Evolution 2.24.3 ... in Picasa you can "send photos in photo tray via email".  Normally, by selecting a few photos, you click on the email icon at the bottom of the screen, and it opens an Evolution email that you can send.

It seems as if this is now broken.  I'm guessing the latest version of Evolution since I have not upgraded Picasa in a while.

Error message I get is:
> "You cannot attach the file `/home/myhomedir/.google/picasa/3.0/drive%5Fc/Documents%20and%20Settings/myhomedir/Local%20Settings/Application%20Data/Google/Picasa2/temp/email/temp%5F2/IMG%5F0003.JPG' to this message.
Error will still open Evolution and an email, but no attachment is there.

Running Intrepid 64bit

Not sure what is happening, as this worked before.  Any help would be appreciated.

---

### Post by gillblu on 2009-02-25
I get the same thing. I believe it all started after Evolution update. Any idea?

---

### Post by Jens007 on 2009-03-03
I have the same problem, is there any solution or do we have to wait for an new update of evolution?

---

### Post by MALEADt on 2009-03-07
As root: create a file */usr/local/bin/picasa-hook-email.sh*, give it 755 permissions and past the following code in it
```
#!/usr/bin/perl

# Fetch input parameters
my $command = shift || exit(1);

# Correct the attachment parameter
$command =~ s/&attach=/&attachment=file:\/\//;

# Call evolution
system("evolution \"$command\"");

# Report back to Picasa
exit 0;
```

Picasa will work now. It was not using the "file://" prefix Evolution requires when attaching files.

---

### Post by Jens007 on 2009-03-09
Thanks for your help, but it did not work. I gave permission to me (it had permission to root) because I don't know the meaning of 755 permission ( I think permission of everything to everyone). I copied everything and created a file. 

Did I something wrong?????

---

### Post by Jens007 on 2009-05-18
Hello,

has anybody an idea, why it does not work? I have done everything you said.

Jens

---

### Post by jyanek on 2009-05-18
> **Jens007 said:**
> Thanks for your help, but it did not work. I gave permission to me (it had permission to root) because I don't know the meaning of 755 permission ( I think permission of everything to everyone). I copied everything and created a file. 

Did I something wrong?????
It worked PERFECTLY for me.  Follow his instructions.  Make sure that ROOT owns the file.

Thanks for the fix!

---

### Post by Jens007 on 2009-05-26
It worked now. I had the permissions wrong. Thanks a lot

---

### Post by Subito Piano on 2010-06-29
so - my evolution (Jaunty Jackalope) will not send pictures in the body of the text.  (I've checked all the appropriaite preferences having to do with html composing and viewing images).  I can insert them and they look fine going out but are not received correctly -- i send them to myself and i can't see the images, even if i attach the images as well as inserting the into the body of the email... see [this post]("http://ubuntuforums.org/showthread.php?t=1324005") .  Is there a way to modify this scripts to allow eveolution to insert images into the emails?

Thanks! [IMG]http://mepislovers.org/forums/images/smilies/snoozer_likelinux_man.gif[/IMG]

---

