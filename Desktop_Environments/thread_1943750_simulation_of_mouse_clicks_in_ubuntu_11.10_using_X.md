---
title: "simulation of mouse clicks in ubuntu 11.10 using X11"
date: 2012-03-20
forum: Desktop Environments
---

### Post by rajplay on 2012-03-20
Hi,

When I had ubuntu 9.04 on my laptop, I had used a piece of code with which I could simulate mouse clicks using X11 libraries(it was working fine). I recently upgraded my ubuntu to 11.10 and now for some reason, the same piece of code is acting very wierd.. The click is simulated when the mouse pointer is on menu bar control buttons(minimize, maximize, close, etc.), but not when inside a window on an icon.. and right click is not simulated at all..

Here is the function that I use :

> void mouseClick(Display *display, Window root, int button)
{
	XEvent event;
	
	if(display == NULL)
	{
		fprintf(stderr, "Error!!!\n");
		exit(1);
	}
	
	memset(&event, 0x00, sizeof(event));
	
	event.type = ButtonPress;
	event.xbutton.button = button;
	event.xbutton.same_screen = True;
	
	XQueryPointer(display, root, &event.xbutton.root, &event.xbutton.window, &event.xbutton.x_root, &event.xbutton.y_root, &event.xbutton.x, &event.xbutton.y, &event.xbutton.state);
	
	event.xbutton.subwindow = event.xbutton.window;
	
	while(event.xbutton.subwindow)
	{
		event.xbutton.window = event.xbutton.subwindow;
		
		XQueryPointer(display, event.xbutton.window, &event.xbutton.root, &event.xbutton.subwindow, &event.xbutton.x_root, &event.xbutton.y_root, &event.xbutton.x, &event.xbutton.y, &event.xbutton.state);
	}
	
	if(XSendEvent(display, PointerWindow, True, 0xfff, &event) == 0) fprintf(stderr, "Error in sending event!!!\n");
	
	XFlush(display);
	
	usleep(100000);
	
	event.type = ButtonRelease;
	event.xbutton.state = 0x100;
	
	if(XSendEvent(display, PointerWindow, True, 0xfff, &event) == 0) fprintf(stderr, "Error in sending event!!!\n");
	
	XFlush(display);
}

Any help on making it work would be appreciated.. :)

---

