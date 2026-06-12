---
title: "Black windows with Beryl"
date: 2007-02-02
forum: Desktop Environments
---

### Post by Russty of Oz on 2007-02-02
I was just wondering if the black windows when using beryl are a "normal" thing or is it just mine that does it?  It usually happens with clicking a link on a page, but occasionally it will do it with even just the terminal and in the attachment you can see that it happened opening Beryl Settings Manager.  In fact just trying to attach the screenshot is a problem as clicking the attach icon also brings up a black window!!

---

### Post by 23meg on 2007-02-02
It's a driver bug. Try launching Beryl with ```
beryl --use-cow --force-aiglx
```

---

### Post by Russty of Oz on 2007-02-02
My whole system froze when I did that, I had to shut it down manually.  

Perhaps it had something to do with it conflicting with Nvidia???

---

### Post by Russty of Oz on 2007-02-02
I tried it again and the terminal says this

russty@russty-desktop:~$ beryl --use-cow --force-aiglx
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options

---

### Post by Russty of Oz on 2007-02-02
And I forget to add to that last post that it still won't work.  :( 

So am I stuck with these black windows?  This is the only thing that bugs me about Beryl, apart from that it is fantastic!

---

### Post by NoXiS on 2007-02-02
Hi

Try this fix which has worked wonders for me with the same kind of problems.

Edit (or create new)  your /etc/drirc file and put the following code into it

```

gksudo gedit /etc/drirc

```

**For ATI Radeon (open source driver):**

```

<driconf>
    <device screen="0" driver="radeon">
        <application name="all">
            <option name="allow_large_textures" value="2" />
        </application>
    </device>
</driconf>

```

**or for binary nVidia Driver:**

```

<driconf>
	<device screen="0" driver="nvidia">
		<application name="all">
			<option name="allow_large_textures" value="2" />
		</application>
	</device>
</driconf>

```

---

### Post by Russty of Oz on 2007-02-02
OK, I put all that in the file as it is, I hope I wasn't suppose to put any particular names in any of those areas?  Anyhow, I have been trying it and so far I have had no black windows, so, fingers crossed, I hope I have done it right.

Thanks for that solution :)

---

### Post by Russty of Oz on 2007-02-02
I spoke too soon!  I just got another black window from clicking a link on a web page. :( 

So, it's back to the drawing board! ](*,)

---

### Post by Steveway on 2007-02-02
In your Beryl-manager change your renderingpath to Copy.
This is only a workaround for the Black-window-bug and we have to wait for Nvidia to fix their drivers.

---

### Post by Russty of Oz on 2007-02-02
OK, I have now done that, but I won't say if it is fixed until later.  

Thanks ;-)

---

### Post by Kent_Geek on 2007-02-03
On my nvidia equipped laptop, setting the "Force AIXGL" setting in the settings manager eliminated the black window problem with much less performance impact than changing the rendering path to "copy".  Both settings fixed the black window, but "copy" rendering was almost unusable.

Has anyone else with this problem found a more satisfactory solution?

More importantly, does anyone know for sure if Nvidia is aware of the problem, and is planning a fix? Or is a fix even possible?

---

### Post by 23meg on 2007-02-03
> Has anyone else with this problem found a more satisfactory solution?No, --force-aiglx is the only thing that makes Beryl usable for me.> More importantly, does anyone know for sure if Nvidia is aware of the problem, and is planning a fix? Or is a fix even possible?Yes, they've acknowledged it and are working on it. As usual, they're not promising to fix it in the next release.

---

### Post by Russty of Oz on 2007-02-03
Well since changing to "copy" I haven't hand any more problems, and there doesn't "seem" to be a performance problem for me using it, but I will try the Force AIXGL thing and see.

I hope Nvidia fix it soon!

---

### Post by Russty of Oz on 2007-02-06
Just thought I would say that I have tried Force AIXGL  instead of Copy, the response time in opening a program, such as Firefox, was a tad slower.  So I have gone back to the Copy method and now everything starts better.   I realize this could just be my computer.  

Russty:)

---

### Post by tegwilym on 2007-02-16
Hey, the "copy" thing workee for me also....mostly.
I got all this working perfectly on my computer at home which is nearly identical to my work machine, but my work computer gets the 'black window' problem.  
I tried the suggestion of setting the rendering to 'copy' and the Beryl features seem to work now.

but......when I'm moving the 'wiggly windows' or any of the other eye candy stuff I get a really bad flicker across the whole screen when doing this.  

Any ideas what might be causing this?  I'm using a DVI output for an LCD monitor, and a VGA to a CRT.  I have 2 CRTs on my home computer, but don't expect this to be the issue of course. 

Tom

---

### Post by belgrave on 2007-11-16
Full solve, with detailed working:

[http://www.deepnerd.com/node/82](http://www.deepnerd.com/node/82)

---

### Post by belgrave on 2007-11-16
in short, if using nvidia drivers, grab the glx new ones from the repos - full detail in the previous link

---

