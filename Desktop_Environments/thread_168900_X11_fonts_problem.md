---
title: "X11 fonts problem"
date: 2006-05-01
forum: Desktop Environments
---

### Post by Nasso on 2006-05-01
I just downloaded Legends: The Game ([http://www.legendsthegame.net/](http://www.legendsthegame.net/)) and installed it using a simple 'sudo sh legends_linux_0.4.1.39.sh' and then tried running it using 'cd /usr/games/legends;./runlegends -console'. The screen goes black for a little while and then returns to normal. In the bottom of the output in the console i can read this;

loadFont: '-*-arial-medium-r-*-*-12-*-*-*-*-*-*-*'
loadFont: '-*-arial-medium-r-*-*-12-*-*-*-*-*-*-*' failed
loadFont: attempting fallback font: '-adobe-helvetica-medium-r-*-*-12-*-*-*-*-*-*-*'
loadFont: couldn't load a fallback font for 'Arial 14'
loadFont: we're now going to fallback to a Courier 10pitch font, but you should try and fix up your X11 fonts!
loadFont: final fontfallback parachute: fallback font: '-*-courier-bold-r-*-*-10-*-*-*-*-*-*-*'
% OK, we can't even fallback to font : '-*-courier-bold-r-*-*-10-*-*-*-*-*-*-*'
CreateFont: request for Arial 14, using
% Fix your font setup. We need Helvetica, and Courier as a minimum, displayable in all sizes by X

How do i fix my fonts?

Im using Ubuntu Breezy Badger.

---

