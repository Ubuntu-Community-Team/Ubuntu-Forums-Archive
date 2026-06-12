---
title: "Japanese, Persian and Arab input and fonts in Ubuntu 9.04"
date: 2009-05-15
forum: General Help
---

### Post by arminius24 on 2009-05-15
Hi everyone,

I am completely new to Ubuntu and Linux just from today, and I actually got into it so I could work with different languages of various alphabets. Unfortunately it has got me very frustrated to try to set up any language other than the Spanish of the install.

How can set up Japanese, Persian and Arab languages in my Ubuntu, so I can type my reports in these languages as well as read them in my computer?

I know someone answered to this question a week ago, but the solution was so out of this world technical for me as a beginner that it is not fitting. Please treat me with kindness as I dont even know about the basics.

Many thanks for any help you could provide to me.

Kind regards

---

### Post by mikewhatever on 2009-05-15
Hi and welcome,

what were the problems with setting up languages?

I really don't know about Japanese, hope someone else can help shortly. I think the utility under System->Preferences->SCIM. Here is a guide for 8.10.
[https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_8.10_using_SCIM](https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_8.10_using_SCIM)
That aside, you can add language layouts under System->Preferences->Keyboard, Layouts tab (second from left).

You can then choose the key combination to change between languages by clicking on Layout Options. The default combination is Alt+Alt, but it didn't work for me, for some reason, so I changed it to the left Alt+Shift, as in Windows.

---

### Post by arminius24 on 2009-05-17
many thanks for you reply. i did set japanese as my language for ubuntu and a japanese keyboard. i restarted it and - as expected - everything was in japanese.

this time a languages icon appeared on the top right, and i could select other languages, for typing in japanese, arabic, and even languages i never selected (punjabi, guarajati, russian, etc.).

because japanese is not my language i dont want my whole os to be in japanese, i just want the languages icon to switch from one language to another.

so i went back to setting english as my language in system/administration, however when restarting in english now the language icon on the top right was gone.

any ideas how to have a permanent language icon there on the top right, so i can switch between languages, and that i can choose which languages are displayed there?

many thanks!

---

### Post by arminius24 on 2009-05-17
Ok, by setting different layouts I am now able to switch from Latin Spanish to Iranian keyboard and input.

Español
&#1601;&#1575;&#1585;&#1587;&#1740;

However, even when adding a Japanese layout keyboard, I am still not able to input Japanese for some reason. When typing syllables like "ja", "pa", "ni", "su", one should see the Japanese moras for these sounds, and I am just seeing Western characters.

Any idea why Japanese needs something else to be done to set it as input keyboard?

Thank you

---

### Post by houman001 on 2009-05-18
I have got my Japanese using SCIM-Anthy, while others like Cyrillic and Persian using Ubuntu's keyboard layout.
[http://www.h4.dion.ne.jp/~apricots/scim-anthy/howto.html](http://www.h4.dion.ne.jp/~apricots/scim-anthy/howto.html)
):P

---

### Post by dmizer on 2009-05-18
The first time you use Anthy for Japanese input, you have to manually change from _A (romaji) to &#12354; (hiragana). After that, you should be able to use the &#21322;&#35282;&#65295;&#20840;&#35282;&#65372;&#28450;&#23383; key to change between inputs. If you don't have that key, generally <shift>+<space> accomplishes the same task.

---

