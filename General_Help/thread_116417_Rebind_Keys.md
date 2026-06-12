---
title: "Rebind Keys"
date: 2006-01-12
forum: General Help
---

### Post by ninocass on 2006-01-12
Is it possible to "bind" keys?

i have mannaged to wreck my dirction arrow keys on my laptop (dont ask!!!!)

the windows key isnt used for anything so i was wondering if it would be possible to bind say

windows key + i = Up
windows key + j = left
windows key + k = down
windows key + l = right

does anyone know if i can do this?

Many thanks

nino

---

### Post by ninocass on 2006-01-12
i have managed to rebind the windows key to right using:

xmodmap -e "keycode 115 =Right"

but is there a way i can get it to use both windows and I ?

Nino

---

### Post by ninocass on 2006-01-17
anyone?

---

### Post by ninocass on 2006-01-19
Managed to get it sorted using:

```

xmodmap -e 'keycode 115 = Mode_switch'

xmodmap -e 'keysym i = i NoSymbol Up     NoSymbol'
xmodmap -e 'keysym j = j NoSymbol Left     NoSymbol'
xmodmap -e 'keysym k = k NoSymbol Down     NoSymbol'
xmodmap -e 'keysym l = l NoSymbol Right     NoSymbol'

```

how would i go about making this permenant as when i restart i need to rebind the keys

---

