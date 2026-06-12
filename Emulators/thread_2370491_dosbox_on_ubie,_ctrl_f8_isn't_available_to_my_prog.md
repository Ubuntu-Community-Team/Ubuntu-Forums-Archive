---
title: "dosbox on ubie, ctrl f8 isn't available to my program?"
date: 2017-09-04
forum: Emulators
---

### Post by seekertom on 2017-09-04
I use an old dos/early win program that relies heavily on macros. Those macros are saved as ascii files, and my key sequence for saving as ascii file is ctrl-f8. It doesn't work. It doesn't do anything at all. Shift f8, for example, my non-ascii save, works fine, as do all the other key combos I've tried so far.

I have this issue using ubie 14 and 17, and on hp pro desktops and my '76 super laptop as well.

Any idea what ctrl-f8 means in dosboxish? or why it won't do my ascii save?

Hope you can help!
st :(

---

### Post by truefacts on 2017-09-07
By default in DOSBox, ctrl-f8 is bound to 'increase frameskip'. Here is a list of the default keybindings: [https://www.dosbox.com/wiki/Special_Keys](https://www.dosbox.com/wiki/Special_Keys)

To remove this keybinding in order to save your files: 
[LIST=1]
[*]In DOSBox, press ctrl-f1 to bring up the key mapper screen. 
[*]Click on 'Inc Fskip' and then either click 'Del' to remove this binding or click 'Add' to change it to something else. 
[*]Click 'Save' and then 'Exit'. 
[/LIST]

This should free up the key combination so it can be used by your program. Consider checking the list of keybindings to make sure you don't have any other conflicts. If you mess up the mapping and want to revert back to the original default keybindings, simply delete the file ~/.dosbox/mapper-0.74.map (filename might differ slightly depending on your DOSBox version).

---

