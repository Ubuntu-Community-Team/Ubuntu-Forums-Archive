---
title: "natty xserver crash and matlab"
date: 2011-08-12
forum: Desktop Environments
---

### Post by huha on 2011-08-12
Hi all,

I'm having troubles with ubuntu Natty.
"Randomly" I'm thrown out back to the log-in page; I saw some threads online talking about xserver crashes but I didn't find any solution.

I noticed it happens more often (but not always) when I use this matlab code to delete all the matlab figures.


Matlab code (not mine):
-----------------------
f = findobj(0);
f(f == 0) = [];
set(f, 'DeleteFcn', '')
f = findobj('Type', 'figure');;
for i = 1:length(f)
   theName = get(f(i), 'Name');
   delete(f(i))
   disp([' ## figure(' num2str(f(i)) ') -- [''' theName '''] -- deleted.'])
end
---------------------------

Anybody has an idea? If you need any info just tell me but maybe include some details, I'm still quite new to linux.

I have a Radeon HD 6370M with proprietary drivers.

Thnaks for any suggestion!

Luca

---

### Post by huha on 2011-08-14
Does all this silence mean that nobody has a clue?

If I posted this in the wrong session or else, please just tell me.

Best,
Luca

---

### Post by TheGeorgian on 2011-11-09
Hello, I had the same problem on the latest ubuntu with matlab. Whenever I was working with figures, I was logged out of the system. I added a startup.m file with the command: 
opengl neverselect

see following links for more info:
[http://www.mathworks.com/matlabcentral/newsreader/view_thread/156009](http://www.mathworks.com/matlabcentral/newsreader/view_thread/156009)
[http://www.mathworks.com/support/tech-notes/1200/1201.html](http://www.mathworks.com/support/tech-notes/1200/1201.html)

so far it works, but we'll see what the long term result is ....

---

