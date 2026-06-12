---
title: "right click - rotate image, how to add option"
date: 2005-08-30
forum: Desktop Environments
---

### Post by jetpeach on 2005-08-30
I'm looking to integrate image rotation into gnome, so I can view thumbnails and simply right-click them to rotate them clockwise or couterclockwise, or perhaps even 180 degrees.  I've searched and searched, but I must be blind, because I can't find an easy way to add this functionality.

So I've figured this much out so far:
This will probably need to be done with the "open with" option, where a program or command is chosen such that the image will be rotated.  I used synaptic to install the library that contained the jpegtran function, which seems necessary, and have played around with custom commands like
"jpegtran -rotate 90 %f > %ftemp; mv %ftemp %f"
which seems like it would work, if Gnome would recognize %f as the filename.  If %f is the name of the file, this command works in the terminal to rotate the image.  So basically I'm trying to figure out the custom command options and could use some help with this.

By the way, does anyone know if Gnome or Ubuntu plan on offering jpg rotation has an option in the GUI on right-clicking images?  I would love it, though I'm sure all the purests out there would say it would be "bloating" things too much... but I love my right-click options as there isn't an easier way to rotate an image...

Thanks,
jet

---

### Post by byronsalty on 2005-09-02
jet,

You can put a script in your ~/.gnome2/nautilus-scripts folder. You then run these by selecting one or more files and then selecting a script to run by right-clicking and you'll see a list of your scripts. When you run on  files selected then they will be fed into your script as multiple arguments.

I also suggest using "convert" to do image manipulation. it does a lot of different things and works on more than just jpegs.

- Byron

---

### Post by xmastree on 2005-09-02
[QUOTE=jetpeach] I used synaptic to install the library that contained the jpegtran function,[/QUOTE]Which library was that? It sounds pretty useful.

It's ok, I found it in libjpeg-progs.

---

### Post by xmastree on 2005-09-02
[SIZE=5]**[COLOR=Red]Got It![/COLOR]**[/SIZE] :cool: 

Rotate_Left
```
#!/bin/sh
for arg 
do
jpegtran -rotate 270 "$arg" > temp.jpg;
mv temp.jpg "$arg"
done

```
Rotate_Right
```
#!/bin/sh
for arg 
do
jpegtran -rotate 90 "$arg" > temp.jpg;
mv temp.jpg "$arg"
done

```Save those two scripts as Rotate_Left and Rotate_Right in:
~/.gnome2/nautilus-scripts
Make them executable, and you're done.  :grin:

More good stuff [here](http://g-scripts.sourceforge.net/index.php)

Update:
Those scripts only work for jpg files, but they will try to act on any file selected, with bad consequenses...  :roll: 
If anyone knows about scripting, and can suggest a way to make it check the filetype first before doing the jpegtran thing, that would be really useful.

---

### Post by byronsalty on 2005-09-03
I did something very similar except when using "convert" the script will work for most (all?) image types. 

I also didn't use the extra file creation/move and everything seems to work fine.

```
convert -rotate 270 $arg $arg
```

---

### Post by xmastree on 2005-09-03
The problem with convert is that it isn't lossless rotation for jpgs. Try rotating one four times and compare it with the original.

So, the best solution would be a combination of the two which detects the filetype. If it's a jpg, do the jpegtran, otherwise use convert.

Can that be done?

---

### Post by doclivingston on 2005-09-04
you could use "file" to determine the file type, and then act accordingly

---

### Post by xmastree on 2005-09-04
```
#!/bin/sh
for arg 
do
 filetype=`file -i "$arg"`
if [ -n "`echo $filetype | grep -i 'jpeg' `" ]; then
 jpegtran -rotate 90 "$arg" > temp.jpg;
 mv temp.jpg "$arg"
else
 convert -rotate 90 "$arg" "$arg"
fi
done
```That seems to work!  :grin: 

Now, where's jetpeach, it seems we have the answer to your original post.

---

### Post by byronsalty on 2005-09-04
very nice addition. I've updated my scripts with your changes to prevent quality loss.

cheers!

---

### Post by stoffe on 2005-09-04
A collection of nautilus scripts are here: [http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/) - there's probably something similar there already, but if not, you might want to add this too. :)

There's also some short instructions on how to create scripts under the FAQ.

---

### Post by xmastree on 2005-09-04
> A collection of nautilus scripts are here: [http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)That's where I got the basics for the one I made.

What I know about scripting can be written on a postage stamp. A very small one, and with a big pen.
So, I looked through the offerings there, took a bit here, a bit there, messed around with all sorts of stupid things which didn't work, and eventually came up with one which did. Then I improved it.

There's one [here](http://g-scripts.sourceforge.net/mirrors/nyquist-nautilus-scripts.tar.gz) in multimedia, but it's huge. I tried it, and it didn't do anthing.  :?

As for mine, there's one more thing it needs.

Look at man jpegtran and you'll see that there's a switch **-trim** which ought to be included.```
jpegtran -rotate 90 -trim "$arg" > temp.jpg
```This is because jpegs are made up of 16x16 pixel blocks. If the image dimensions aren't exactly divisible by 16 there will be problems. Using -trim will cut off the excess. Example, I tested it with a 400 x 265 image. Untrimmed there was a strip along one edge which ought to have been on the other side. Trimmed it came out at 400x256 but looked better.

I guess this won't normally be an issue, since pictures from a digital camera will be the right size (max resolution of my D70 is 2000x3008. 3008 seems a strange figure until you realise why), and anything cropped (like my examples) will have been rotated first.
Scanned images could be any size, but are likely to have been scanned the right way up in the first place.

---

### Post by jetpeach on 2005-10-17
Sorry was gone for a bit but thanks for the information guys, this will help me much.  I'm downloading and setting up the scripts on my new Breezy setup now.
jetpeach

---

### Post by SendDerek on 2007-01-21
This looks like a pretty old thread, but I just wanted to drop in and say thank you to xmastree for the scripts that you created to rotate images in nautilus.  So, THANK YOU!

They work great!  Now, if only there was a way to incorporate or convert these scripts into buttons that you see in a toolbar of some sort!

If there are any updates in the world of photo management, please let me know!  I'm subscribing to this thread to see what else there may be!

---

### Post by zigx on 2007-03-15
[http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/Rotate-Mirror_pictures](http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Image/Rotate-Mirror_pictures)


That did the trick for me!!

also you should install jhead ( sudo apt-get install jhead )

---

