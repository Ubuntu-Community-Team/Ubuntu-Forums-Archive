---
title: "Beta testing schedule"
date: 2007-03-15
forum: Development CD/DVD Image Testing
---

### Post by Henrik on 2007-03-15
The ubuntu archives have now been [frozen]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2007-March/000262.html"), leading up to the beta release. The first candidate ISO images may appear ***tomorrow***, or more likely ***Monday***.

**[SIZE=4]The processes[/SIZE]**

At that point we'll be focusing on verification testing of the beta-candidate ISOs. We are looking to confirm that it has built OK, that it boots and runs as expected and will be looking out for major bugs. It is valuable to check the [list of bugs being tracked for beta]("https://launchpad.net/ubuntu/+milestone/7.04-beta") so we avoid filing duplicates and can confirm that assumed fixed bugs are indeed gone. We are also very interested in regressions: something that worked last week but no longer does.

A given ISO image may need to be rebuilt several times as bugs are discovered. This may be related to hardware issues or desktop applications. If a serious bug is found in the Kubuntu version of Ubiquity say, then the following images will need re-building and re-testing: Kubuntu desktop i386 and Kubuntu desktop amd64. The DVDs will be re-built as well, though at a slightly lower priority.  If the problem lies with the amd64 kernel then absolutely all the amd64 images will be redone. etc. This will continue until we are confident that all the images are good. Likely Tuesday and Wednesday next week. The [plan]("https://wiki.ubuntu.com/FeistyReleaseSchedule") is to release the beta on Thursday.

[SIZE=4]**What you should do**[/SIZE]

Make sure you have the images that you will be testing downloaded already, ready to be updated with rsync. On similar ISO images the download speed with rsync can be as little as 10% of the normal download. Read more about rsync [here]("https://help.ubuntu.com/community/RsyncCdImage") and [here]("http://www.ubuntuforums.org/showthread.php?t=386269"). Make sure you are familiar with the ISO testing procedures ([1]("https://wiki.ubuntu.com/Testing/InstallMethods"), [2]("https://wiki.ubuntu.com/Testing/Short"), [3]("https://wiki.ubuntu.com/Testing/Long")) and the [reporting system]("https://wiki.ubuntu.com/Testing/ReportingResults"). 

Then just wait ... If you have [signed up]("http://www.ubuntuforums.org/showthread.php?t=383067") for a test case then we will email you when candidate images are ready and we will post updates here. If you are logged in to #ubuntu-iso or #ubuntu-devel on freenode you can watch the action as it unfolds :)

---

