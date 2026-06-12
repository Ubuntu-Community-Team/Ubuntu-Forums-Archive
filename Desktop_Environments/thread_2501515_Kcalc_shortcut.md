---
title: "Kcalc shortcut"
date: 2024-10-11
forum: Desktop Environments
---

### Post by sunday28 on 2024-10-11
After upgrading Kubuntu to 24.10, the standard keyboard shortcut for the calculator does not work.
I tried ctrl+K, success.
How to return the ability to use the standard keyboard shortcut?

---

### Post by ActionParsnip on 2024-10-11
What is the `standard keyboard shortcut` please?

---

### Post by sunday28 on 2024-10-11
There is a "calculator" key on the keyboard.
KCalc is attached to it in KDE.
After updating to 24.10, using this key does nothing: KCalc simply does not run.
It is also not possible to reassign KCalc to this key.

---

### Post by norbert-r78 on 2024-10-12
I confirm, the &#8216;Calculator&#8217; button does not work.

---

### Post by ActionParsnip on 2024-10-13
Does the keyboard have a make and model?
If you run
```

xev

```
Then press the button, does it create events?
If you go into the shortcut settings, can you assign the button as a shortcut?

---

### Post by sunday28 on 2024-10-15
> [COLOR=#000000]Does the keyboard have a make and model?[/COLOR] 
Logitech K270
> [COLOR=#000000]Then press the button, does it create events?[/COLOR]
[COLOR=#000000]If you go into the shortcut settings, can you assign the button as a shortcut?[/COLOR]
Unfortunately, no. This button was fine in KUbuntu 24.04.
I suppose this is not the fault of KUbuntu and the keyboard.
Probably, this is some kind of bug in Plasma 6.
Tested in Ubuntu Live, the calculator starts with this key without any problems.
Thank you for your help and feedback.

---

### Post by deadflowr on 2024-10-15
What does Settings >> Keyboard >> Shortcuts show for kcalc?
I see it as having no shortcut by default but simple to set.

I looked at this on a system I upgraded from 24.04 to 24.10, logging into both wayland and X11 sessions.
Setting a shortcut worked fine on both.
(I set it with ctrl+k, but if there is some special key you usually set, I don't know how that plays out)

---

### Post by sunday28 on 2024-10-15
> [COLOR=#000000]I see it as having no shortcut by default but simple to set.[/COLOR]

You are right.
I can also easy set a combination, for example, Ctrl+K.
But the Logitech K270 PC keyboard has a separate key on which the calculator icon is actually drawn.
This key is used in both KDE and Gnome to launch Kcalc or Gnome-calculator, respectively.
After upgrading Kubuntu to 24.10, I can no longer use this key.
It also fails to assign it to KCalc.
I'm inclined to think this is a problem in Plasma 6.
Here in the discussion, **norbert-r78** also confirmed the problem.
Since 6.1.5 is the last version in 6.1, this bug will probably not be fixed in KUbuntu 24.10.
Maybe I'm wrong. In any case, I thank everyone for the answers and I think that using a different keyboard shortcut to run the calculator for a while is not too difficult. ;)

---

### Post by 1fallen on 2024-10-15
Definitely not a Plasma 6 problem, mine works with the>>{Fn+F12} which is how you described "keyboard has a separate key on which the calculator icon is actually drawn."
Did you try to reset it?
```
[FONT=monospace][COLOR=#000000]**plasma-desktop **[/COLOR][COLOR=#54FF54]**6.2.0-1.1**[/COLOR][COLOR=#5454FF]**(plasma)**[/COLOR][COLOR=#54FFFF]**[installed]**[/COLOR]
    KDE Plasma Desktop
[/FONT]
```[FONT=monospace]
[/FONT]

---

### Post by sunday28 on 2024-10-16
> [COLOR=#000000]Did you try to reset it?[/COLOR]
It's impossible: Kcalc had no shortcut after upgrade to 24.10.
It worked by default in 24.04.
And it works fine in Ubuntu Live 24.10 as I wrote earlier.
After upgrade to Kubuntu 24.10 no possibility to assign this button to run KCAlc.
Only another shortcut: ctrl + K, for example, and so on.
I saw on Reddit similar problem, but about Plasma 6.0.
KUbuntu 24.10 has 6.1.5.

---

