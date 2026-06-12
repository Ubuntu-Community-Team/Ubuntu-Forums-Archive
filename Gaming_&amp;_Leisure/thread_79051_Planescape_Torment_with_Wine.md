---
title: "Planescape Torment with Wine"
date: 2005-10-19
forum: Gaming &amp; Leisure
---

### Post by crypto178 on 2005-10-19
Hello!
Feeling a bit nostalgic (ok the game isn't that old, it's just that there aren't too many good RPG's coming out these times), I tried to install Planescape Torment in breezy. 
According to the wineHQ.org apps DB and Frank's Corner, the game should run pretty fine with Wine. Anyone runs it? can post a few advices? I tried many settings with winecfg but no avail. When started, the game just displays an empty error box and quits. 
If it is revelant, I'm using the 4 CD version (I've heard there' is a 2 CD version too) patched to 1.1. 
Thanks for any input.

---

### Post by der_joachim on 2005-10-19
Take a look at the URL below:

[http://liflg.org/?catid=7&gameid=40](http://liflg.org/?catid=7&gameid=40)

Thank you Loki! I haven't tried it yet, because someone borrowed my Torment CDs and never returned them. :-(

---

### Post by crypto178 on 2005-10-19
It looks like it uses WineX, I'll give it a try tomorrow after compiling cedega CVS. 
I didn't think of that option, thanks :)

---

### Post by Havoc on 2005-10-19
Yup, I'm using it, and it plays GREAT!
I remember having some crashes, but I think those had something to do with my NO-CD patch.You need not install using a Loki installer, It installs perfectly.

If you're having problems with the X cursor not wanting to go away, just press CTRL+ALT+Right, and then back to the workspace where Planescape is on.That should work.

Oh, and I'm that pothead Alex Ferguson offering wrong pointers in the PS:T page in wineHQ. :D

---

### Post by crypto178 on 2005-10-19
Did you have to make anything special to get it to run ? what are the steps required to get it running from a fresh breezy install?

What I did is :
Install wine from synaptic
wine /media/cdrom/Setup.exe
<it installs fine, left directory as default>
wine Torment_patch_v1.1.exe
<patch installs fine>
and then 
insert cd2
cd ~/.wine/drive_c/Program Files/Black Isle/Torment
wine Torment.exe

But It didn't work :(
Then I made changes in the torment.ini file as explained on the wineHQ page and also changed some settings in the winecfg utility, with no luck unfortunatly.

---

### Post by Havoc on 2005-10-19
What did you get, a "Runtime Error" or something?

Cause if you did, then do this:

Copy the cd you used to install the game into a folder like..."CD" inside your torment folder.Then, change your "Torment.ini" file to make the part pointing towards the CD1 look something like this 

"CD1:=c:\Program Files\Black Isle\Torment\CD"

without the quotes.Save the file.Then, run autorun.exe and select "Play".

It SHOULD work.If it doesn't, tell me more.

---

### Post by crypto178 on 2005-10-20
Ok, I deleted the .wine folder and started again.
When installed, I copied the cd1 and cd2 in the Torment folder and edited the ini file accordingly.
Then I start autorun.exe (the one in the torment folder that I copied following the instructions), I click on "play", the game seems to be starting, the screen resolution changes to a very low one, then changes back to my desktop resolution again and a message box appears asking me if it's ok to continue without 16bit mode. I click Ok, then it loads for a little while and eventually an empty error message box (one with no text) appears. If I don't click on OK, more of these start to appear, when I click on OK the game exits.
I tried again from a terminal to get some output :
```
fixme:vxd:VXD_Open Unknown/unsupported VxD L"sice.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"ntice.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe1ae48)->(00020022,00000011)
fixme:wave:DSD_CreateSecondaryBuffer (0x7fe07ee0,0x7fadacf4,12,0,0x7fe3ba8c,0x7fe3bb9c,0x7fe3ba68): stub
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fe1a8d8)->(00000000,00000008)
fixme:wave:DSD_CreateSecondaryBuffer (0x72791220,0x7fadab70,12,0,0x6b8fd4b4,0x7fe07404,0x6b8fd490): stub

```
I think that the last line appears at the same time as the mysterious error message, so it may be the problem.

---

### Post by Havoc on 2005-10-20
Heh, I remember that problem, more about it further on. ;) 

Anyways, here's what I did.

1)I popped in my 1st CD, the one you use to install.Installed like a charm.
2)Installed the 1.1 patch (You don't need it if you've got the 2 CD game).Installed like a charm.
3)Made a "CD" folder inside the "Torment" folder.
4)Copied EVERYTHING from CD1 to the CD folder.
5)Changed my Torment.ini file to point to the "CD" folder for the CD1.Also, changed those lines in the end from zero to one.
6)Popped in CD2, and ran "autorun.exe" inside the CD folder.Selected "Play".

I'm done!

Now, for the CDs, anything more than the CD1 needs a NO-CD crack along with the changes in the "Torment.ini" file.That is because, even if Torment sees all the files, it still prompts you to insert the CD, for obvious reasons.If torment does not see any cd inside but sees all the files, it tells you about the color and crashes.

So, you can either start Planescape with ONLY the first CD copied, and the other one already inserted, or copy ALL CDs to your computer, point to them in the .ini file, and replace the original Torment.exe with a cracked one.

The second solution has a trick.If you're low on disk space, or whatever, you can copy all CDs in the same folder.That will save you some space since many files in the CDs overlap.BUT, I've had some problems using this method (Not just putting them in the same folder, but generally copying them all to my HDD and running using a NO-CD crack).Sometimes, NPCs seem invisible, because the game cannot find the graphics files or whatever.

So, in case you're extremely bored of changing CDs all the time, don't do the "Copy all the CDs" method.It's not gonna destroy your game, but sometimes, It's annoying. ;)

---

### Post by crypto178 on 2005-10-20
Ok! it works! thanks a lot for the help :)
It appears that some default path settings in winecfg were wrong, and the game couldn't find the cdrom drive. So I fixed those and now the game runs fine, thanks again.

---

### Post by remick182 on 2005-12-16
Hey, I wasn't sure if you'd check back to the original thread that you participated in a couple months ago regarding PS:T, but I had a question seeing as you got it working for you.
I installed everything (4 CD game): Install disc, 1.1 patch, 'CD' folder with copied CD1, edited .ini file, and made changes in my winecfg file to have it recognize Z: as a cdrom at /media/cdrom0 instead of a hard disk and the game loaded up normally.  Once I finish creating a new character, I get prompted to insert CD2 into the drive...but it's already there.  Otherwise it wouldn't have gotten that far.  Is there something else that I should be doing?  Thanks for any help.

---

### Post by Anonii on 2006-08-23
Greetings,

I have installed Planescape with the 2CD version, applied the NO-CD crack, BUT:

I can pass the first check allright, and I can move to the character creation screen, but then I have to insert the second cd to my c: (wtf) drive, which is my main drive, my drive_c.
I tried pasting all the CD2 contents in there, but it wont work. And from what I noticed it changes the drive to other people, so can I change it to something more normal, like "insert disk 2 to d:", or do you have any kind of fix for that? :/

This is my Torment.ini:
> [Alias]

HD0:=c:\Program Files\Black Isle\Planescape - Torment\

CD1:=c:\Program Files\Black Isle\Planescape - Torment\CD

CD2:=c:\Program Files\Black Isle\Planescape - Torment\CD

CD3:=c:\Program Files\Black Isle\Planescape - Torment\CD

CD4:=c:\Program Files\Black Isle\Planescape - Torment\CD

And these are my drives throu winecfg:

[IMG]http://img.photobucket.com/albums/v148/Assa-san/drives.png[/IMG]


Thank you very much, for your help :)

---

### Post by Anonii on 2006-08-24
Well, nevermind,

I fixed it by reseting wine and reinstalling the program, I then had to insert the disc on z: which I redirected to /mnt/cdrom, mounted the iso there, and finished ^_^

Thanks, anyway!

---

### Post by Moosferatu on 2006-09-13
Has anyone else gotten this error?

```

fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x180d00) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16ddc8)->(0x10024,00000011)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16err:clipping:CLIPPING_UpdateGCRegion hVisRgn is zero. Please report this.
```

Any ideas?

---

### Post by Redemption042 on 2006-12-02
Yeah, I'm also having this issue.  Looks like a bug has been filed with WineHQ.  We'll see what happens.

---

### Post by Moosferatu on 2006-12-02
I don't think it's possible to get it working on the newer versions of wine due to the change in direct draw, though I wasn't able to get it working on 9.15 either.  bah.

---

