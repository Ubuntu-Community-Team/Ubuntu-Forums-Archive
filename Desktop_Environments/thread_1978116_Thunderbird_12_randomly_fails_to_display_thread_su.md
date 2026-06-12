---
title: "Thunderbird 12 randomly fails to display thread summaries"
date: 2012-05-11
forum: Desktop Environments
---

### Post by uziel on 2012-05-11
I have a problem with Thunderbird 12.0.1 in Xubuntu 12.04 (although it was exactly the same before upgrade from 10.04). The problem is that the thread summaries on collapsed threads often fail to display, and instead the first message in thread is shown.

More precisely, when I choose a thread for the first time after launching the program, the summary shows up, but in a rather useless version, namely consisting only of message senders' names and timestamps (so no actual message summary is shown). After a thread is expanded (either by clicking one of those senders' names or ordinarily in the message list) and some individual message shown, then choosing some collapsed thread again does not display the summary, but only the thread starter message. I've noticed that some actions (ie. going to another tab and back) can restore the ability to display these "useless" thread summaries, but again even these disappear after an individual message from some thread is shown.

I use vertical view if it's relevant and mail.operate_on_msgs_in_collapsed_threads is set to true, although IIRC this setting did not alter anything.

(Ideally, in the end I want the Thunderbird Conversations add-on to work, but as I guess it relies on the thread summary feature and has completely no effect when installed and enabled.)

A (temporary) workaround is to downgrade (to TB11 in 12.04, in which case TB Conversations do work, and TB3 in 10.04). I would rather see it resolved in some way, TIA.

---

### Post by mozjonathan on 2012-05-12
Hi,

I'm the author of Thunderbird Conversations. It should work, of course, in Thunderbird 12: please make sure you're running the latest version (2.3.2 or something like that). If it's not, please see [https://github.com/protz/GMail-Conversation-View/wiki/Debugging-Conversations](https://github.com/protz/GMail-Conversation-View/wiki/Debugging-Conversations) and send me an email with extra information.

Thanks,

jonathan

---

### Post by uziel on 2012-05-17
I have reupgraded to 12 again and now everything works. This looks pretty random.

---

