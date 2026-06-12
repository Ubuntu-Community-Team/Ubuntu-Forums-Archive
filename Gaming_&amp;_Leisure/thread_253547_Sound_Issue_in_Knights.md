---
title: "Sound Issue in Knights"
date: 2006-09-08
forum: Gaming &amp; Leisure
---

### Post by jdunn on 2006-09-08
I'm using Kubuntu Dapper.  I can't get Knights sound to work.  When I run from the console, I get some aRTS error and Knights crashes.  The only way I can get Knights to run is if I uncheck "Enable Audio" in Knights.  I fixed the sound archives (KSDefault, KSProvence, KSKnights) but despite that, I get these errors:


file /build/buildd/arts-1.5.2/./mcop/flowsystem.cc: line 120 (virtual void Arts::RemoteScheduleNode::connect(const std::string&, Arts::ScheduleNode*, const std::string&)): assertion failed: (!fs.isNull())
KCrash: Application 'knights' crashing...


and after the initial crash, I get this when I run Knights a second time with audio enabled


knights: WARNING: audio::audio: Can not create Arts::SoundServerV2exit

---

