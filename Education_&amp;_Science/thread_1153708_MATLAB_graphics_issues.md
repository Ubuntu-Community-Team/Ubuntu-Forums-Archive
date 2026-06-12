---
title: "MATLAB graphics issues"
date: 2009-05-09
forum: Education &amp; Science
---

### Post by lethalfang on 2009-05-09
Anyone has any idea what is going on there?

When I start MATLAB 2009, I get this message: 

Warning: Initializing Handle Graphics failed in matlabrc.
This indicates a potentially serious problem in your MATLAB setup,
which should be resolved as soon as possible.  Error detected was:
MATLAB:badsubscript
Attempted to access monitors(1,:); index out of bounds because size(monitors)=[0,4]. 
> In matlabrc at 100

Line 96 to 106 in the file matlabrc.m is the following: 

try
    % Initialize Handle Graphics including default paper size settings.
    hgrc
catch exc
   warning('MATLAB:matlabrc:InitHandleGraphics', '%s\n%s\n%s\n%s\n%s', ...
       'Initializing Handle Graphics failed in matlabrc.',...
       'This indicates a potentially serious problem in your MATLAB setup,',...
       'which should be resolved as soon as possible.  Error detected was:',...
       exc.identifier,...
       exc.message);
end


When I try to graph in MATLAB, I get black background when it's supposed to be white.

My video card is ATI Mobility Radeon HD 2600, and I have installed the ATI proprietary driver.

Edit: by the way, I haven't had this problem before, so I figure it might've been caused by some later updates to the Ubuntu 9.04 64-bit.

---

### Post by ad_267 on 2009-05-09
Do you have Compiz enabled? Disabling it can fix all kinds of problems.

---

### Post by lethalfang on 2009-05-10
With the help of a friend of mine and this online entry: [http://remmirath-en.blogspot.com/2008/05/matlab-warning-initializing-handle.html](http://remmirath-en.blogspot.com/2008/05/matlab-warning-initializing-handle.html) , I have sort of made a fix by editing **hgrc.m** file in matlab, by commenting out: 

```
monitors = get(0, 'MonitorPositions');
```

and replace it with

```
monitors = [0,0,1280,800;1281,801,1280,800];
```

But this solution is monitor-specific and not all that elegant, so if someone knows of a better fix, I'd greatly appreciate it. 

Thanks

---

### Post by jarlz0r on 2009-12-02
Awesome, your fix stops it from triggering the "index out of bounds", and doesn't seem to mess anything else up. Thank you! :)

See [http://www.mathworks.com/access/helpdesk/help/techdoc/ref/rootobject_props.html#MonitorPositions](http://www.mathworks.com/access/helpdesk/help/techdoc/ref/rootobject_props.html#MonitorPositions) for reference on what you are supposed to put into the matrix for multihead systems.
Since the function fails at the very first line, it never reaches the part where it sets the color scheme to white :)

---

