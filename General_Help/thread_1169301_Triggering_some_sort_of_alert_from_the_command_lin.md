---
title: "Triggering some sort of alert from the command line?"
date: 2009-05-25
forum: General Help
---

### Post by Vunutus on 2009-05-25
Essentially, I have some console program running on one of my workspaces. Most of the things that scroll by I don't care about but a few I do. I already have a way to trigger SOME action when those events occur, but I need some way to notify myself even if I'm on another workspace. Is there any way to do something like creating a message box on my current workspace from the command line? I'd prefer some way to do it that's built into Ubuntu but if I need to download some program to do it I'm open to suggestions.

---

### Post by maheshasolkar on 2009-05-25
zenity may be what you are looking for:
```

  zenity --info --text="Something significant happened!"
```

For more info on zenity:

```
  man zenity
```

---

### Post by Vunutus on 2009-05-25
> **maheshasolkar said:**
> zenity may be what you are looking for:
```

  zenity --info --text="Something significant happened!"
```

For more info on zenity:

```
  man zenity
```

Excellent, that's exactly what I was looking for.

The best part is that I had heard about zenity before and even known what it did but for some reason didn't think of using it :popcorn:

---

### Post by glotz on 2009-05-25
Other options include xmessage, notify-send and aosd-cat.

---

