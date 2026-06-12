---
title: "System hangs every time I use YouTube on a ThinkPad T450"
date: 2019-09-06
forum: Desktop Environments
---

### Post by thranulsterman on 2019-09-06
Dear all,

I'm a happy user of Xubuntu and have found it hassle-free through most of the years that I used it. However, unfortunately I've run into a severe issue on my ThinkPad T450. Previously I asked for help in the #xubuntu channel and was kindly advised; now I'm posting here to continue the conversation with a wider audience.

[SEE HERE FOR SOLUTION]("https://ubuntuforums.org/showthread.php?t=2426276&p=13898955#post13898955")

The issue is when I use FireFox to watch YouTube it is almost guaranteed that the system will hang, become unresponsive and then require a hard reset.

I'm using Xubuntu 19.04.

The laptop is a ThinkPad T450. It has a standard configuration except that I installed a SSD. I ran a comprehensive self-test using the Lenovo BIOS' testing feature and everything was given the all-clear.

I'm not the only owner of a T450 in my household. Curiously, this other T450 which runs Xubuntu 18.04 (LTS) does not manifest the same issue. This system also uses FireFox as its browser.

I was advised to check the system logfiles. The only mention of anything likely in the logfiles is the **xsession-errors** file:

```
(nm-applet:1321): Gtk-WARNING **: 21:01:42.453: Can't set a parent on widget which has a parent

(xfce4-panel:1291): xfce4-panel-CRITICAL **: 21:01:45.450: panel-window.c:2245 (panel_window_active_window_geometry_changed): expression 'WNCK_IS_WINDOW (active_window)' failed.

(/usr/lib/firefox/firefox:1631): dconf-WARNING **: 21:01:47.129: Unable to open /var/lib/snapd/desktop/dconf/profile/user: Permission denied
[Child 1577, MediaDecoderStateMachine #1] WARNING: Decoder=7f15d3e94c00 Decode error: NS_ERROR_DOM_MEDIA_FATAL_ERR (0x806e0005) - RefPtr<mozilla::MozPromise<RefPtr<mozilla::MediaTrackDemuxer::SamplesHolder>, mozilla::MediaResult, true> > mozilla::MediaSourceTrackDemuxer::DoGetSamples(int32_t): manager is detached.: file /build/firefox-9JL5Vx/firefox-69.0+build2/dom/media/MediaDecoderStateMachine.cpp, line 3309
[Child 1577, MediaDecoderStateMachine #1] WARNING: Decoder=7f15d3e94c00 Decode error: NS_ERROR_DOM_MEDIA_FATAL_ERR (0x806e0005) - RefPtr<mozilla::MozPromise<RefPtr<mozilla::MediaTrackDemuxer::SamplesHolder>, mozilla::MediaResult, true> > mozilla::MediaSourceTrackDemuxer::DoGetSamples(int32_t): manager is detached.: file /build/firefox-9JL5Vx/firefox-69.0+build2/dom/media/MediaDecoderStateMachine.cpp, line 3309
```

That error mentioning Firefox is repeated about fifteen times very near the end of the logfile; concurrent with the hang.

I'll welcome any help or suggestions.  

:guitar:

---

### Post by mörgæs on 2019-09-06
Hi, welcome to the fora.
Does Chromium behave the same way?

---

### Post by Autodave on 2019-09-06
Are you running ad blockers?  Some of them are extreme memory hogs.  Try uBlock and disable the rest of them.

---

### Post by thranulsterman on 2019-09-07
> **mörgæs said:**
> Hi, welcome to the fora.
Thank-you.

> **mörgæs said:**
> Does Chromium behave the same way?
Interestingly, I installed my preferred WebKit browser which is Vivaldi. About 25 minutes into a SpaceX launch in HD and it hasn't crashed. I suppose this is now pointing to a FireFox issue.

> **Autodave said:**
> Are you running ad blockers?  Some of them are extreme memory hogs.  Try uBlock and disable the rest of them.
My extensions of choice are: uBlock Origin, Privacy Badger and Decentraleyes. I could try FF with them disabled and see what happens.

---

### Post by thranulsterman on 2019-10-20
Dear all,

I finally fixed this issue by disabling the security chip on my laptop. It turns out that it was interfering with the Ubuntu OS. So if you're getting random system hangs and crashes on a Thinkpad T450, try disabling the security chip in the BIOS. Besides, it doesn't seem as if it offers any actual security benefit to the everyday user. Likely this chip only works in a Windows enterprise setting.

Looks like we can lift the blame off the good folks at Mozilla.

Overall system stability has improved too! I'm honestly so chuffed to have this fixed, now I can use my laptop in perfect peace of mind.

Thanks for your help and direction.
Happy computing,
Thran

---

