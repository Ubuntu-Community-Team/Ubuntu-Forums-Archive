---
title: "register thumbnailer in gnome config"
date: 2010-09-30
forum: Desktop Environments
---

### Post by Aegluin on 2010-09-30
Hi!
I try to implement thumbnails for files from a Wine program in order to integrate it better in Ubuntu. The Program is Sketchup which creates *.skp files in a binary format, but I found a ruby script that can extract the thumbnail (*.png).

Now I wanted to register it in the gnome configuration according to the following instruction:
[http://library.gnome.org/devel/integumbnailer.html]("http://library.gnome.org/devel/integumbnailer.html")

It works perfect if I execute the script manually (package *ruby* installed, script is executable):

```
ruby ~/.wine/skp-thumbnailer.rb /home/user/test.skp /home/user/test.png
```

Creates successfully a thumbnail test.png from the file test.skp.
With the following commands, I registered the script, but it doesn't create thumbnails automatically:

```
gconftool-2 -s /desktop/gnome/thumbnailers/application@wine-extension-skp/enable --type=bool true
gconftool-2 -s /desktop/gnome/thumbnailers/application@wine-extension-skp/command --type=string "ruby ~/.wine/skp-thumbnailer.rb %i %o"
```

Now my question is how to find the mistake. Do I need to copy the script into /usr/bin ? Apart from that, would it be possible to create it as a shell script (without *ruby* requirement)? If I knew how to translate it into .sh, I would prefer that.
Many thanks for help!

---

### Post by rtlong on 2010-11-08
I am not positive of this, but I believe haven't used tho proper argument placeholders in your gconf key. If you'll look at the other thumbnailers, they all use %s %u and %o. %s is size, %u is the URI of the file to be thumbnailed, and %o is the output filename. I think you could just ignore the size argument, and generate the same size regardless what nautilus wants. But, I am not sure if that works. 

In regards to making this a shell script, I think that would be *possible*, but it certainly won't be pretty (at least not in the manner that I might do it, but, I, myself, am much more comfortable in Ruby). Why do you want not to use a Ruby script?

Another thing I would change is the location of your script file. I would put it in either /usr/bin or ~/bin (you may need to make that folder). There is no reason for it to be mixed in with WINE. Also, it may be best to use a full path instead of the tilde abbreviation.

Finally, and here is the most important part, your Ruby script won't work if it is fed a URI, which, as I said before, is what gnome will send the thumbnailer. I can help you fix it, though, if you want.

---

### Post by Aegluin on 2010-11-08
Hi!
many thanks for the help! I solved it already some weeks ago after nobody replied.
The problem was the mime type had to be application/x-wine-extension-skp and the script must be placed in /usr/bin. I finally used a python variant of the script that I found somewhere on the internet and now it works.

---

### Post by rtlong on 2010-11-08
Okay! Good to hear you got some help and got it fixed. Could you mark the thread as having been solved, please?

---

