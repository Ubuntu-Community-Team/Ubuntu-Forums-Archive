---
title: "Modifying AWN Applets"
date: 2009-01-02
forum: General Help
---

### Post by 5BallJuggler on 2009-01-02
I'm having a play with some applets in AWN, and just stumbled onto the weather one, 
it's working fine, but I can't change the Opacity of the 5day forecast, there are no options to do it in AWN, and I cant do it in the gconf-editor (Ubuntu) either, does anyone have any ideas how it could be done?

I've attached a screenshot so you know what i'm talking about.

---

### Post by kaivalagi on 2009-01-02
I think you need to make a request to the author asking for that feature in the settings...

I have had a quick look at the forecastdialogs.py source and I think it would require some changes to the cairo context code I think...

I am not familiar with cairo so can't be certain, but I don't think there is any way to have what you want without a code change

---

### Post by 5BallJuggler on 2009-01-02
Thanks, I'll try to get the authors details.

---

