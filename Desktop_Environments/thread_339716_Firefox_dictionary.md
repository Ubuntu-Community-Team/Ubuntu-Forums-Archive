---
title: "Firefox dictionary"
date: 2007-01-16
forum: Desktop Environments
---

### Post by Edward The Bonobo on 2007-01-16
Does anyone know how to select the dictionary that Firefox uses for its spell checker?  Mine doesn't seem to be set to English (or French, German, Italian, Spanish, Czech...)

---

### Post by hanexar on 2007-01-21
You need to right click an underline word and go to the language menu under the suggestion, and set the dictionary to the desired language. You can add multiple one, quite useful.

---

### Post by edmund on 2007-02-11
When I tried this, the only option available under the Languages menu was "Add Dictionaries...", even though I'd installed the British English Dictionary and restarted Firefox.

I fixed it by changing:
  user_pref("spellchecker.dictionary", "en_US");
to:
  user_pref("spellchecker.dictionary", "en_GB");
in prefs.js in the Firefox profile area (~/.mozilla/firefox/<profile>.default).

---

### Post by edmund on 2007-02-11
P.S. You need to exit Firefox before changing any of the settings in prefs.js, otherwise your changes will be overwritten when you close Firefox.

---

### Post by Lunar_Lamp on 2007-06-20
You can do it in a slightly simpler way also:

In Firefox go to about:config and search for spellchecker.dictionary and change the value of "en_US" to "en_GB", and then restart firefox (though I'm not sure if that's necessary).

---

### Post by NostradamusZen on 2008-07-19
> **Lunar_Lamp said:**
> You can do it in a slightly simpler way also:

In Firefox go to about:config and search for spellchecker.dictionary and change the value of "en_US" to "en_GB", and then restart firefox (though I'm not sure if that's necessary).

Yes, a firefox restart is necessary :)

---

