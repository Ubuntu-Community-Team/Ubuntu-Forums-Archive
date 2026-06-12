---
title: "File Formats"
date: 2009-05-16
forum: General Help
---

### Post by ktechman on 2009-05-16
I just copied a cd (data) and needed an .iso image but it gave me an .toc instead so I burned it to disc and it works like it should.   My question what is the difference in the extensions?

---

### Post by cariboo on 2009-05-16
Have a look [here]("http://filext.com/file-extension/TOC") for info on a .toc file. In the future you can use one of the cd burning applications to create an .iso file, or the way I do it is to insert the cd and open a terminal and type:

```
sudo dd if=/dev/scd0 of=cdname.iso
```

---

### Post by jespdj on 2009-05-16
Instead of dd, you could use the command readom ("read optical media"). For example:
```
readom dev=/dev/scd0 f=/path/to/image.iso
```
As far as I know, readom works better than dd for this because it does error checking (I don't know the details of this).

[This page](http://www.commandlinefu.com/commands/view/1396/create-a-cddvd-iso-image-from-disk.) says:
> Many like to use 'dd' for creating CD/DVD iso images. This is bad. Very bad. The reason this is, is 'dd' doesn't have any built-in error checking. So, you don't know if you got all the bits or not. As such, it is not the right tool for the job. Instead, 'reaom' (read optical media) from the wodim package is what you should be using. It has built-in error checking.

---

