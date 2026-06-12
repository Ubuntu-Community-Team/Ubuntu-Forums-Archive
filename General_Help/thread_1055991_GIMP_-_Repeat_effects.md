---
title: "GIMP - Repeat effects?"
date: 2009-01-31
forum: General Help
---

### Post by xiroV on 2009-01-31
Hi all :)

I'm going to make a change to A LOT of images, but it's actually the same "change", or "effect" I'm going to use on all of them, so i wanted to ask if anyone know if it's possible to edit multiply images with the same effect easily?

I know that Adobe Photoshop got some function, which works something like this:

1. Press some kind of recordbutton, which records all your effects and so on.

2. Do whatever effects on the picture that you want to apply.

3. Press some button to make the recording stop.

Now, as far as I know, you can click a button each time you want to apply the recorded effects to a picture.

Back to the question: Does anyone know a similar function in GIMP? Or some suggestions on how to do it?

---

### Post by Keyper7 on 2009-01-31
I think [Script-Fu](http://docs.gimp.org/en/gimp-concepts-script-fu.html) might be what you're looking for.

Unfortunately, my GIMP-fu is not very strong, so I can't do much to help you other than pointing you that link.

---

### Post by Mohamedzv2 on 2009-01-31
If you make the new effect on a layer, then just copy that layer and paste it.

If you are using filters, there is a repeat filter. 

Other than that, there is no easy way to repeat the effects.

---

### Post by Lunx on 2009-01-31
> **Mohamedzv2 said:**
> If you make the new effect on a layer, then just copy that layer and paste it.

If you are using filters, there is a repeat filter. 

Other than that, there is no easy way to repeat the effects.

Depends on your idea of easy I guess ;) I've been using GIMP for a couple of years and pretty sure Script-fu will do what you want for sure (actually it's the only other way I can think of doing it in an automated fashion). Trouble is I only have a very rudimentry understanding of what it's about, let alone writing it. But as suggested, you can create new layers to copy and paste (I often create simple layers that I keep in xcf format so I can re-use them in other projects, great for maintaining continuity when I'm working on a particular theme)

---

### Post by saulgoode on 2009-01-31
[Dave's Batch Processor]("http://members.ozemail.com.au/~hodsond/dbp.html") is capable of performing many typical manipulations on multiple images. Otherwise, it is not uncommon for people to make a request for a custom-written script in places such as the [GIMP Plug-in Registry]("http://registry.gimp.org/forum") or the [GIMPtalk forums]("http://www.gimptalk.com/forum/").

---

### Post by xiroV on 2009-01-31
I don't wanna start learning a new scripting language atm, so it would be great if you had more suggestions :D

What I need, is a script to repeat "Colorize" and "Brightness/Contrast".. 

Can Dave's Batch Processor do that? and they wrote I can install it by running "make install".. but that doesn't work.. I know it's a newbie question, but can someone make an example please? :)

---

### Post by xiroV on 2009-01-31
Lawl.. nevermind my last message.. just found it in a package on synaptic xD sorry..

---

### Post by Lunx on 2009-01-31
> **xiroV said:**
> I don't wanna start learning a new scripting language atm, so it would be great if you had more suggestions :D

What I need, is a script to repeat "Colorize" and "Brightness/Contrast".. 

Can Dave's Batch Processor do that? and they wrote I can install it by running "make install".. but that doesn't work.. I know it's a newbie question, but can someone make an example please? :)


Here you go, you can do some basic batch editing at the command line

[http://www.gimp.org/tutorials/Basic_Batch/](http://www.gimp.org/tutorials/Basic_Batch/)

Doesn't really help I know, still looks like a bit of a learning curve (but not too steep)

Had a look at Dave's Batch Processor, you have to compile the package and install it to your local GIMP plugins directory ie in  ```
/home/<yourname>/.gimp-2.6/ plugins.
```.

---

### Post by Lunx on 2009-01-31
> **xiroV said:**
> Lawl.. nevermind my last message.. just found it in a package on synaptic xD sorry..

I went looking and didn't see it at first, then found it it in **gimp-plugin-registry**. I see there's a couple of other batch editors that may do some of what you want. Look in Synaptic for **phatch** and **squash**

---

