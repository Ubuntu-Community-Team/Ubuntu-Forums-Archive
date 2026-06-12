---
title: "Dual Monitor Desktop Icons on Right Hand Screen Using an Offset in Gnome"
date: 2011-03-09
forum: Desktop Environments
---

### Post by skarard on 2011-03-09
Hey Ubuntu People,

I am loving the Dual Monitor output on my PC. There is only one problem. That is the icons on the desktop auto generate on the left screen. This is frustrating because it's not always turned on. Also When resizing in Gimp the Resize Dialog pops up on the right hand side. I hear they are working on sorting out a default monitor option in 04.11.

I have been looking in to the Desktop Icon offset problem and have found on: [http://git.gnome.org/browse/nautilus/tree/libnautilus-private/nautilus-icon-container.c]("http://git.gnome.org/browse/nautilus/tree/libnautilus-private/nautilus-icon-container.c")

Line 324 - 386:

```
	if (nautilus_icon_container_get_is_fixed_size (container)) {
		/*  FIXME: This should be:

		container_x = GTK_WIDGET (container)->allocation.x;
		container_y = GTK_WIDGET (container)->allocation.y;
		container_width = GTK_WIDGET (container)->allocation.width;
		container_height = GTK_WIDGET (container)->allocation.height;

		But for some reason the widget allocation is sometimes not done
		at startup, and the allocation is then only 45x60. which is
		really bad.

		For now, we have a cheesy workaround:
		*/
		container_x = 0;
		container_y = 0;
		container_width = gdk_screen_width () - container_x
			- container->details->left_margin
			- container->details->right_margin;
		container_height = gdk_screen_height () - container_y
			- container->details->top_margin
			- container->details->bottom_margin;
		pixels_per_unit = EEL_CANVAS (container)->pixels_per_unit;
		/* Clip the position of the icon within our desktop bounds */
		container_left = container_x / pixels_per_unit;
		container_top =  container_y / pixels_per_unit;
		container_right = container_left + container_width / pixels_per_unit;
		container_bottom = container_top + container_height / pixels_per_unit;

		icon_get_bounding_box (icon, &x1, &y1, &x2, &y2,
				       BOUNDS_USAGE_FOR_ENTIRE_ITEM);
		item_width = x2 - x1;
		item_height = y2 - y1;

		icon_bounds = nautilus_icon_canvas_item_get_icon_rectangle (icon->item);

		/* determine icon rectangle relative to item rectangle */
		height_above = icon_bounds.y0 - y1;
		width_left = icon_bounds.x0 - x1;

		min_x = container_left + DESKTOP_PAD_HORIZONTAL + width_left;
		max_x = container_right - DESKTOP_PAD_HORIZONTAL - item_width + width_left;
		x = CLAMP (x, min_x, max_x);

		min_y = container_top + height_above + DESKTOP_PAD_VERTICAL;
		max_y = container_bottom - DESKTOP_PAD_VERTICAL - item_height + height_above;
		y = CLAMP (y, min_y, max_y);
	}

	if (icon->x == ICON_UNPOSITIONED_VALUE) {
		icon->x = 0;
	}
	if (icon->y == ICON_UNPOSITIONED_VALUE) {
		icon->y = 0;
	}

	eel_canvas_item_move (EEL_CANVAS_ITEM (icon->item),
				x - icon->x,
				y - icon->y);

	icon->x = x;
	icon->y = y;
}
```

I am just wondering if anyone would know a way of setting an offset for 1080 for the desktop icon container in ~/.gtkrc-2.0

Any info out there?

Thanks,

---

