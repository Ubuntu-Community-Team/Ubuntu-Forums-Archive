---
title: "Notification Popup second colour - Can I change it?"
date: 2009-01-09
forum: General Help
---

### Post by NEUR0M4NCER on 2009-01-09
As the title says; the notification popups have two colours - the background, which I can change in Appearance->Colours, and another yellowish colour on the left of the box... is there any way of changing that second colour?

---

### Post by Ivo Moelans on 2009-01-09
I don't think it is possible. I could be wrong, but I seem to remember having read somewhere that the second color is hard coded in the application.
BTW, I also have read that the whole notification system will be revised for Jaunty.
However, at the moment notification uses two themes. The one you use is probably "ubuntu". There is also "bubble" and in this theme both colors (and the text color) follow the colors of your gtk theme. You can change the notification theme in Configuration Editor (*Application&#8594;System Tools&#8594;Configuration Editor* or Alt+F2 and type *gconf-editor*). Then go to *apps&#8594;notification-daemon*. In the left pane under *theme* you can type *bubble* or *ubuntu*.

Some themes define the notification theme in the *index.file*. You can *change* that with text editor. If it isn't already defined but you want to use one of these notification themes with a gtk theme you can *add* this line at the bottom of the index.file

```
NotificationTheme=bubble
```

Hope this helps.

---

### Post by NEUR0M4NCER on 2009-01-09
Thanks - i'm pretty much set on my theming, so modifying it might be the way to go (changing the notification theming option). Didn't know this was the case. Also good news about Jaunty; is that a Gnome thing, or is Ubuntu sorting things out?

---

### Post by Ivo Moelans on 2009-01-09
_[Here]("http://www.markshuttleworth.com/archives/253")_ you can read about the plans on Mark Shuttleworth's own blog.

---

### Post by NEUR0M4NCER on 2009-01-10
... wow. That is some discussion over there. I'm very tempted to throw my 2 pence in as-well, but i'm not exactly knowledgable in such areas, so...

Thanks for the heads up anyway. It's good that M. Shuttleworth's actually in there 'hands on'. I guess I can live with the notifications for now...

---

### Post by Ivo Moelans on 2009-01-10
You're welcome.

---

