---
title: "Firefox/Flash player   Crash :("
date: 2009-02-20
forum: General Help
---

### Post by -=[gizmo]=- on 2009-02-20
Hay I'm still new Ubuntu. Now every since I installed the flash-player add-on for Firefox 3.0.6.

Now every time i see a flash applet Firefox crashes.

I don't know where to start to try fix this problem.

Any help thanks.
:popcorn:

---

### Post by trlkly on 2009-02-24
I assume you tried to install the flash plugin using Firefox, instead of through the repositories. It's an easy mistake to make.

You'll need to delete the bad flash plugin. But first, let's make sure that's really the problem. Open up Firefox. Go to Tools > Add-ons, and click on the Plugins icon. Somewhere in the list below, you'll find an item that mentions flash. Click the Disable button inside that item.

Restart Firefox (just to be sure) and try going to a Flash site. **Don't install anything!** Just make sure the browser no longer crashes.

Go ahead and try this, and post you're results. I want to make sure you're still having problems before I delve into the more complex part of explaining how to fix it.

---

### Post by -=[gizmo]=- on 2009-02-24
Wow thats for the Reply.
It done what you said, i HAD TWO of them?

I disabled both, and tried one at a time, they both seamed to have problems :(. Also don't know is this helps but i installed Opera The flash works but i get no sound? 

Would be awesome if you could help.

---

### Post by trlkly on 2009-02-24
The fact that sound doesn't work in Opera may mean problems down the road. But we'll wait and see.

You had two plugins? What were they called? It's important, so I can figure out where they are installed on your hard drive.

And did disabling them both keep Firefox from crashing when you visited a flash site? (For example, try to open a youtube video. It won't work, but Firefox should at least not crash.)

---

### Post by deepclutch on 2009-02-24
if you installed flashplayer 10 ,please purge(remove) libflashsupport.

---

### Post by -=[gizmo]=- on 2009-02-24
Shockwave flash 9.0 r48
and
Shockwave slash 9.0 r999

----------------------
Now about the crashing it dose not Crash every time i see a Flash app.
But when I run You tube the sounds jumps and fezzes and then the Hole Computer lags(witch is crazy i run 4G Ram and AMD +5000)
 It dose not always crash on a flash app like i was saying, some times it wont but very rarely. But im 100% sure its the flash not firefox.

---

### Post by deepclutch on 2009-02-24
if you are using a 64-bit Linux distro ,why not switch to adobe flashplayer 10 beta for x86_64 ?I am using it and currently not seeing any problem.while flash9 depends on nspluginwrapper which you may need to install.check there.

---

### Post by -=[gizmo]=- on 2009-02-24
No only 32 Bit

---

### Post by deepclutch on 2009-02-24
remove your current "libflashplayer.so" files from /usr/lib directory.remove flashplugin package(s) installed completely.open the terminal and try below thing to find if any libflashplayer.so is residing:
```

 find      /usr/lib      -name libflashplayer.so
```


. then download the file from [**adobe**]("http://get.adobe.com/flashplayer/") site and extract libflashplayer.so file to Desktop.copy the file to /usr/lib/firefox/plugins/ directory.that will do the job.

---

### Post by -=[gizmo]=- on 2009-02-24
I deleted troughs files 
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/opera/plugins/libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so

and then installed Flashplayer 10, But i didnt add on to Firefox?
How do i delete the firefox flash addons ?

---

### Post by trlkly on 2009-02-24
Well, Deepclutch has covered finding and deleting the files, so the old flash shouldn't be installed in Firefox anymore.

Are there any more references to Flash Player **9** in Addons? If there are, then we've still got more files to delete.

As for Flash Player 10, if it doesn't show up in Addons, you're going to have to copy the new libflashplayer.so file to /usr/lib/firefox-addons/plugins 

That should do it. Tell us how you get on.

If you still find that sound doesn't work, we may have a few more problems.

---

### Post by deepclutch on 2009-02-24
well @-=[gizmo]=- : 32-bit Ubuntu you are using?.now ,copy the flash 10 "libflashplayer.so" file to below directory:
**/usr/lib/firefox-3.0.6/plugins/ **
this is where mine resides.after copying to that directory , quit firefox and invoke it again.in address bar type  **about:plugins**,see whether flash is listed now.

---

### Post by trlkly on 2009-02-24
Don't get confused. The two different places we're telling you are actually the same folder. Either one should work, but if one doesn't, try the other.

---

### Post by umechanism on 2009-02-24
> **deepclutch said:**
> well @-=[gizmo]=- : 32-bit Ubuntu you are using?.now ,copy the flash 10 "libflashplayer.so" file to below directory:
**/usr/lib/firefox-3.0.6/plugins/ **
this is where mine resides.after copying to that directory , quit firefox and invoke it again.in address bar type  **about:plugins**,see whether flash is listed now.

I have been following this thread with great interest because I'm having the same crashing problems.  I have followed the suggestions here and after deleting the .so file and reinstalling as directed, I still have crashing.  "About: plugins" gives me this:

```

Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r22
```

Is this correct?

---

### Post by -=[gizmo]=- on 2009-02-25
Ok guys, i have deleted and replaced Flash, and yes i have used flash 10. 

Shockwave flash 9.0 r999, is still there even tho i have deleted them all? And why isn't 10 showing up? All and all it still crashers when i load up youtube your any other flash app.

Im soo lost :(

---

### Post by jmagsho on 2009-02-25
I too am having problems after the software update (yesterday I think it was) to the latest version of Flash from the repositories.

---

### Post by trlkly on 2009-03-01
Sorry gizmo. I've been away. The problem you're having is that your old flash plugin is still installed.

Check your about:plugins (type that into the Firefox address bar) and find out the filename of the Flash plugin. Search your entire Filesystem for that file, and delete all of them.

Once flash is completely uninstalled, you shouldn't have problems with crashing. 

Now, try out the flash in the repositories. Go to System > Administration > Synaptic Package Manager. Use the search button to search for "Flash". Click on the checkbox, and choose the option Mark for Installation. Then click the apply button.

Hopefully, this will sort out your flash problems. If not, just keep trying this thread. I had a lot of problems getting flash running the first time, too.

---

### Post by trlkly on 2009-03-01
> **jmagsho said:**
> I too am having problems after the software update (yesterday I think it was) to the latest version of Flash from the repositories.

Do you know what version of flash you ran before the update? I'm going to assume it was the default 10.0r15.

I'll upload my old flash plugin. Search for all your libflashplayer.so, and replace them with my older version. (Use Places > Search to find all of yours).

ETA: The file was too big to attach, so I uploaded it to my webserver. [Get it here.](http://trlkly.drivehq.com/flash.zip) (sorry about the slow download times).

Let me know when you get it. I don't really want to leave it up for very long. (This goes for umechanism, too.)

---

### Post by -=[gizmo]=- on 2009-03-01
ok thank you Trlkly, i did download load that file, but i didn't need it. 

$ sudo rm /usr/lib/swfdec-mozilla/libswfdecmozilla.so
$ sudo rm /usr/share/ubufox/plugins/libswfdecmozilla.so

thats what i found and deleted.
witch left me with only flashplayer 10. and it works fine :D

youtube up and running.

Thanks heaps for your help.

:guitar:

---

### Post by trlkly on 2009-03-02
Glad to help.

---

