---
title: "Ubuntu 14.04 unity launcher scroll to focus changed"
date: 2014-06-01
forum: Desktop Environments
---

### Post by I.Bun.Tu on 2014-06-01
I posted about this on Ask Ubuntu because I thought a majority of users would benefit from a solution but I never seem to get any help on Ask Ubuntu so I will post here.

Basically I've noticed the focus behaviour when you scroll over the launcher icon of an app with multiple windows open has changed. In the past scrolling over the icon would bring all the windows of that application into focus in succession (one after another).

As of 14.04 this behaviour appears to be changed so that if other applications are open underneath, or were previously in focus, only one window of an applicatioin with multiple windows will stay in front or in focus.

For example if you have firefox open and 3 nautilus windows and you want to scroll on the nautilus icon to bring all 3 windows up, it will bring one up after the other but when the next one comes up, the previous one goes behind firefox. If you are staring at the desktop with all application minimised then scrolling will bring up all 3 nautilus windows as expected (or as it did in the past).

Here is a link to the ask ubuntu question: [http://askubuntu.com/questions/451959/ubuntu-14-04-change-scroll-to-focus-to-not-minimize](http://askubuntu.com/questions/451959/ubuntu-14-04-change-scroll-to-focus-to-not-minimize)

someone else bothered by the functionality made a video uploaded to youtube so you can see the issue and it may be better explained in the askubuntu post.

I've installed Ubuntu 14.04 on about 5 or 6 different machines now and they all have the same functionality. As far as I understand, this is how scroll to focus now work for everyone in Ubuntu 14.04. I'd appreciate to know if this is not the case and if some people still retain the old functionality.

Most importantly I need a resolution to this issue. It's had an extreme hamper on my productivity in Ubuntu, especially trying to transfer files. Instead of scrolling 2 clicks over nautilus to make 2 windows appear that I want to transfer a file from one location to another in, I can scroll to make one appear and then I have to right click the launcher and select the other folder from the context menu.

I mean, one of the main draws of Ubuntu is the focus on productivity and making the distro as fast to use as possible by introducing new ways to do things. At first I disliked the lack of minimise option from the launcher but with scroll to focus it's changed the way I handle and DE and increased my productivity immensely (along with the dash and the HUD). I'd really love to get the old scroll to focus functionality back (it's been the same for me on all machines in 12.04, 12.10, 13.04, 13.10 and has only now just changed in 14.04).

Thank you. Please let me know what more information I can provide to help troubleshoot.

---

### Post by bapoumba on 2014-06-01
I wont be able to comment on the focus behavior as I'm not using Unity. My own file browser (PCManFM) supports tabbing. I'd be surprised if nautilus does not. This is how I do it, have several tabs in only one PCManFM instance.
I understand this is not what you are asking, but may be some way to control your productivity in the meantime :)

---

### Post by I.Bun.Tu on 2014-06-01
Ty, nautilus supports tabbing. I use nemo myself. Thanks for the suggestion, I use new tabs and new windows for different purposes. I often find it more practical to be able to view multiple folder contents at once as opposed to having to jump back and forth, being only able to view the contents of one folder at a time (as with tabbing).

---

### Post by I.Bun.Tu on 2014-07-01
Hey guys. Still no resolution to this issue. I can't believe no one else is finding this to be an extreme problem. I don't know if it's gotten worse or if I'm just noticing more issues with it but when there's a few different programs open with multiple windows each, sometimes scrolling on on program will make windows of another program come up behind it but in front of other windows, depending on what was last behind it.

I would love to receive some information from Ubuntu developers on if there was an intention to change the scroll to focus behaviour or if new updates in 14.04 have broken the original scripts responsible for allowing this.

I think it's kind of sad that this issue hasn't been addressed after a couple of months already.

---

### Post by I.Bun.Tu on 2014-07-04
Is there any way I could pay a Ubuntu developer to work with me for a day or however long it takes to resolve this issue? Or make an agreement to donate a certain amount of money to Canonical? I'm getting really frustrated with the lack of support I'm receiving on this issue and am running into problems with it several times an hour. I used to just pull up all the windows up a program with a simple swipe of my touchpad to scroll through them all and now I have to right click and select them all individually.

---

### Post by mc4man on 2014-07-04
I believe this has occurred to to 2 "Design" bug fixes that actually eliminated scrolling on an inactive launcher icon that had an open unfocused window(s)
That lead to an option in ccsm to allow scrolling on such icons (i believe the option is default enabled), but it maintains the existing stacking order rather than restack as each scrolled window is brought to focus/top

here's the report that contains links to causative bugs in description
[https://bugs.launchpad.net/unity/+bug/1288957](https://bugs.launchpad.net/unity/+bug/1288957)

What you could do is file a new bug referring to above bug stating that as windows are scrolled (brought to top) the stacking order should be 'reset'

Edit: taking this bug into account (& resulting changes), then it may be that what you get now is the best you'll see.
[https://bugs.launchpad.net/unity/+bug/1081843](https://bugs.launchpad.net/unity/+bug/1081843)

As best I can see most of the changes where meant to protect users with poor motor controls who may mouse over an icon & **inadvertently** scroll

---

