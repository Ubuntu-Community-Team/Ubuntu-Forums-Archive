---
title: "Nautilus file types in Trusty (MIME)"
date: 2015-03-22
forum: Desktop Environments
---

### Post by heyup on 2015-03-22
Migrating from Precise (Gnome Fallback) to Trusty (Gnome Fashback) I find nautilus has a number of annoying changes, including changes to file type descriptions.

For example:

File type = Trusty = Precise

.mht = Unknown = web archive
.deb = Archive = Debian package
.odt = Document = ODT document
.dxf = Image = DXF vector image
.gz = Archive = Tar archive
.bz2 = Archive = Tar archive
.kmy =  Unknown = KMyMoney file 
.pdf = Document = PDF document
.m4a = Audio = MPEG-4 audio
.mp3 = Audio = MP3 audio
.iso = Unknown =raw CD image

These changes in nautilus from Precise to Trusty appear to me to be a downgrade rather than an upgrade.
   
Is there an easy way of changing the file descriptions, or am I stuck with files being described by nautilus as unknown or not very informative descriptions ?

---

### Post by dino99 on 2015-03-22
That's the difference made by gtk3

---

### Post by mc4man on 2015-03-22
Don't think this is gtk or any actual change, possibly something local. Tested here with the ubuntu session nautilus & the various gnome session's nautilus - nothing has changed  & reported types are as expected.
Maybe log in to a guest session & check there.

---

### Post by heyup on 2015-03-22
Screenshot of what I see showing some files I copied from Precise into Trusty. 

[ATTACH=CONFIG]260833[/ATTACH]

This is a clean install of Trusty (logged in as myself) using Gnome Flashback Session, that I'm testing.

---

### Post by heyup on 2015-03-22
Log in as Guest makes no difference. 

An .odt file is shown as Document rather than ODT document.

---

### Post by mc4man on 2015-03-22
Didn't realize you meant in list view. If you want mime displayed then you could enable it in  List Columns

---

### Post by heyup on 2015-03-23
Apologies. It was unclear from my first post that I was referring to list view in nautilus.

You are right. I could enable MIME type in list columns, but that was not really the outcome I was looking for.

In Trusty the file type column shows the 'category' of the file type whereas in Precise the file type column shows the 'description' of the file type. So in Trusty an .m4a and .mp3 file is shown as Audio ('category') whereas in Precise the same files are shown as MPEG-4 audio and MP3 audio ('description'). 

I was looking for a solution to revert nautilus back to showing the file description rather than the file category.

BTW your PPAs to patch nautilus are much appreciated:
[http://launchpad.net/~mc3man/+archive/ubuntu/nauty-mods]("http://launchpad.net/~mc3man/+archive/ubuntu/nauty-mods")
[http://launchpad.net/~mc3man/+archive/ubuntu/nauty-hacks1]("http://launchpad.net/~mc3man/+archive/ubuntu/nauty-hacks1")

---

### Post by mc4man on 2015-03-23
If you're inclined to track down when & possibly why the "Type" column changed then could see if it's possible to return. Though it may have been either too long ago to be changed or not done intentionally in which case a lost cause...
(i've a new patch I've been using but haven't inc. yet - it makes that floating bar that shows up when a file has been selected disappear on mouse-over rather that switch sides. Could be useful for list view in some circumstances

---

### Post by heyup on 2015-03-24
Think I found the change in /usr/share/doc/nautilus/NEWS.gz

> Major changes in 3.5.92 are:
Change the Type column to only show basic type information

Details here:
[http://git.gnome.org/browse/nautilus/commit/?h=gnome-3-6&id=a530d6f71fe285ebf2b2a0af4eb53829a6b6d8e4]("http://git.gnome.org/browse/nautilus/commit/?h=gnome-3-6&id=a530d6f71fe285ebf2b2a0af4eb53829a6b6d8e4")

Seems the changes were made not because of an actual bug, but because of developers preferences. Details here:

[http://bugzilla.gnome.org/show_bug.cgi?id=683722]("http://bugzilla.gnome.org/show_bug.cgi?id=683722")

---

### Post by heyup on 2015-03-24
It would have been better if the developers had added an option in list view for the file category type  (i.e. basic type information) rather than to replace the option of the file description type with the file category type.

The developers did a similar thing with the date time-stamp i.e. remove the option of full date and time and replaced with just the date.

---

### Post by mc4man on 2015-03-24
Is this what you're looking for? - screen
If I'll fool around a bit either tonight or tomorrow as it seems not hard to do though kinda weird so need to ck.
I added a Type (detailed) column hoping it would show type_detailed. Instead Type is now detailed & Type (detailed) shows as the current Type does, ie. generic mime groups.
Would prefer that they are switched..., ie Type as now, Type (detailed) as in screen...

Edit: fixed, silly typing mistake - see screen 2 which shows orig.  - Type &  new -  Type (detailed)
The floating bar is definitely a pita at times so will be adding patch to remove on mouse-over to ppa - screen 3 show it gone from scr. 2 with mouse-over

If a test build & a little use work out ok this & floating bar patch  will be in the nautilus improved ppa (nauty-hacks ) - done, if any issues let me know

---

### Post by heyup on 2015-03-24
That looks fine. I couldn't have done that - don't have enough coding know-how.

---

### Post by mc4man on 2015-03-24
The ppa build is done & published (nauty-hacks & nauty-mods
So both Type & Type (detailed) are available for use, the default will be as before, Type

---

### Post by heyup on 2015-03-25
I notice that enabling or disabling a column via Preferences &#8594; File Preferences -> List Columns does not occur in the user's folder. The user has to enable or disable a column (by a right click the list column). Changes to the order of the columns does work. This bug also applies to nauty-hacks.
 
mc3man. I'm not expecting you to solve this bug.

---

### Post by mc4man on 2015-03-25
I had noticed that some time ago, will take a look at again

Edit: think I figured out, try new builds.  See if in edit > preferences > list columns the changes are global, (ie. your new "Default")  & also  that any one folder can be set individually if desired in it's  column > r. click, ect...

---

### Post by heyup on 2015-03-25
Edited. 
The bug is still there. When I'm in my user name folder, Edit -> Preferences -> File Management Preferences -> List Columns doesn't work to the columns in my user name folder, but otherwise works globally (bar one sub-folder!!!). It seems to work OK when in home folder or sub-folders (except for my user name folder).

As I said I don't expect you to solve this bug. It came about when the developers made the change in 3.5.92 update.

---

### Post by mc4man on 2015-03-25
Hmm, I know that the floating bar patch caused some issues with getting user set displayed columns to work properly, since I  reverted it things are working as expected in an ubuntu session (unity
So here - nautilus > Edit > Preferences > List Columns sets the new user defaults & if I have a folder that didn't use them & I wanted it to then,  in that folder > r. click on column bar > dropdown > Use Default fixes that. 
If I get a chance will try  a gnome session on a different install to see how it works out.

---

### Post by heyup on 2015-03-26
I'm testing on a clean desktop install of Trusty to which I've also installed Gnome Fashback session i.e. installed gnome-session-flashback (or gnome-panel) indicator-applet-complete indicator-application indicator-session ubuntu-artwork ubuntu-session ubuntu-settings (if not already installed).

At log in, click icon by user name, gives options to log into either (1) Ubuntu (default) i.e. unity (2) Gnome flashback (with metacity) or (3) Gnome flashback (with compiz). I log into (2) Gnome flashback (with metacity); I don't use unity or compiz.

When I purge nauty-hacks the bug is still there. So the bug isn't caused by nauty-hacks. The bug affects the user's folder.

I use Precise on another partition. In Precise, Edit -> Preferences -> File Management Preferences -> List Columns allows enabling or disabling a column, or changing the order of the columns, and the changes occur immediately and globally to all folders.

In Trusty, Preferences -> File Preferences -> List Columns allows enabling or disabling a column, or changing the order of the columns, but enabling or disabling a column doesn't occur in my user name folder; it only occurs in other folders. I have to right click to enable or disable columns in my user folder.

I thought the bug is likely to have been introduced with this commit [https://git.gnome.org/browse/nautilus/commit/?h=gnome-3-6&id=a530d6f71fe285ebf2b2a0af4eb53829a6b6d8e4]("https://git.gnome.org/browse/nautilus/commit/?h=gnome-3-6&id=a530d6f71fe285ebf2b2a0af4eb53829a6b6d8e4") but I suppose it could have been introduced by later changes.

As you say, a right click in user's folder is all that is required to make things look OK.

---

### Post by mc4man on 2015-03-26
Probably something else, they (gnome devs) changed a lot since then & have little concern for older nautilus releases
(- If you look closely at that commit you'll notice it created the attribute_detailed_type (Type (detailed)), which made it pretty easy to add. Why they created it but didn't add it as an option absolutely no clue. Maybe it's in latest upstream nautilus, maybe not.

---

