---
title: "Problems with OWA / Exchange Server 2010 on Karmic"
date: 2010-04-27
forum: Desktop Environments
---

### Post by JudyB on 2010-04-27
We recently switched from using Lotus Notes to Exchange Server 2010 as our email system. I am running Karmic (64-bit) on a Mac Pro so I have limited options available for local email clients unless I want to use a Windows box via remote desktop or VMWare etc.

Although I have successfully set up Thunderbird for email, this doesn't handle calendars for Exchange Server 2010 so I am also using Outlook Web App (from Firefox).
One problem I have found is that the scrollbars for the Inbox view are always disabled, although OWA clearly recognises Firefox as a supported browser for its "Premium" support.
**Edit:** Using the arrow keys or Page Down don't work for paging through the Inbox either.

Comparing notes with my colleagues it seems that Firefox 3.0.0.19 on Jaunty is OK, as is a newer beta version of Firefox (I think 3.7) running on Lucid once the User Agent string has been adjusted.

I was running Firefox 3.5.9 on Karmic and I have also upgraded to 3.6.3 but that doesn't help. Since Firefox on other versions of Ubuntu are OK it looks like this problem might be linked to Karmic, but that guess may be wrong.

Does anyone have any suggestions about how I might be able to fix this problem?

Thanks,

Judy

P.S. Using something else instead of Exchange Server 2010 is not an option here...

---

### Post by paulisdead on 2010-04-27
Well, if it works fine in Lucid, I'd probably just do the upgrade to that, since it goes final this week anyways.  If you install the release candidate, it'll only be a few updates to get up to the final when it comes out.

If you don't want to go that route, you could just enable the firefox/thunderbird PPA, to get firefox 3.6, just google around for it.  Also maybe, if you don't use OWA premium things will work better.

As for the calendar.  I had the best experience with Thunderbird and the Lightning add on.  By itself, lightning will give you a local calendar, and you can reply to meeting requests and all that, and they insert into the calendar fine.  The thing is, it's only a local calendar, and won't sync with the server.  If you have admin access to the server, you can install Davmail on the server, and setup lightning to connect to it.

You can run Davmail on the the client itself, but I always had issues with that, and was never able to get it to work.

---

### Post by JudyB on 2010-04-28
Thanks for the suggestions.

I do want to look at Lucid fairly soon, but I don't want to go to Lucid immediately since experience with upgrading to Karmic (admittedly from Hardy) took a few days to get all of the build tools correctly updated/reinstalled and I don't want to try and do the upgrade in a rush.

Yes, using OWA Lite instead of OWA Premium does "fix" the problems with disabled scrollbars.

For now I am running Remote Desktop into a Windows box as the best overall solution, but I will have a look at the Lightning plugin to see how that works for me. The main thing I am missing at the moment is good meeting notifications...

---

### Post by JudyB on 2010-04-30
A colleague has now found the solution to this problem:
> ... zoom in above 100% (i.e.  View > Zoom > Zoom In) - that seems to  make it all work

(obviously his Google search skills are better than mine)

---

