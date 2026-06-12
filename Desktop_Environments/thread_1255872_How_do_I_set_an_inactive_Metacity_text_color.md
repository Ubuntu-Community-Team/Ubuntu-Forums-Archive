---
title: "How do I set an inactive Metacity text color?"
date: 2009-09-02
forum: Desktop Environments
---

### Post by fredbird67 on 2009-09-02
I'm working on a variation of an existing Metacity theme that, for the active window, displays white text on the GTK theme's "selected" color and, for the inactive window, displays black text on the GTK theme's "background" color.

But there's one problem:  The variation I'm going for is a black variation of said theme, where it has white text on a black background for the active window, and gray text on a black background for the inactive window.

The active window looks just fine, but on the inactive window, I'm getting black on black, and that's obviously not what I want, as it's hard to read that way.  Does anyone know how to override that in the Metacity theme?

Thanx in advance,
Fred in St. Louis

---

### Post by dumblebee100 on 2009-09-02
> **fredbird67 said:**
> I'm working on a variation of an existing Metacity theme that, for the active window, displays white text on the GTK theme's "selected" color and, for the inactive window, displays black text on the GTK theme's "background" color.

But there's one problem:  The variation I'm going for is a black variation of said theme, where it has white text on a black background for the active window, and gray text on a black background for the inactive window.

The active window looks just fine, but on the inactive window, I'm getting black on black, and that's obviously not what I want, as it's hard to read that way.  Does anyone know how to override that in the Metacity theme?

Thanx in advance,
Fred in St. Louis

post your metacity theme ..I can help you ....every metacity is different in its terms ..so what I tell you may not be the solution for you ....
since every metacity has their own styles ..like giving colours in a different way ..like bgcolor ..some give colour definitions whereever necessary ...so please give me your metacity-theme.xml
I will try to help you

---

### Post by fredbird67 on 2009-09-02
OK, here's what I've got so far:

<?xml version="1.0"?>
<metacity_theme>
	<info>
	  <name>Unity</name>
	  <author>bvc: button source, xfce4 default theme, and modified</author>
	  <copyright>GPL</copyright>
	  <date>December 2005</date>
	  <description>Can we have Unity please?</description>

		<!--	Original theme, SystemG, by andymorum.deviantart.com

					[ Comments from andymorum]
					Just a tiny something for the community to say 
					thanks for all the hard work that has gone into 
					Gnome, XFCE, Linux, Firefox and	all the other 
					great open source projects that have made my 
					life easier.
					
					:D
		-->

		<!--	Please note that some of the XML in this file is based
					on that used in the 'Smokey' Metacity theme.
		-->
	</info>

	<frame_geometry name="normal" title_scale="medium">
	  <distance name="left_width" value="3"/>
	  <distance name="right_width" value="3"/>
	  <distance name="bottom_height" value="3"/>
	  <distance name="left_titlebar_edge" value="2"/>
	  <distance name="right_titlebar_edge" value="5"/>
	  <distance name="title_vertical_pad" value="5"/>
	  <border name="title_border" left="2" right="5" top="1" bottom="0"/>
	  <border name="button_border" left="0" right="0" top="1" bottom="0"/>
	  <distance name="button_width" value="26"/>
	  <distance name="button_height" value="20"/>
	</frame_geometry>

	<frame_geometry name="shaded" title_scale="medium">
	  <distance name="left_width" value="3"/>
	  <distance name="right_width" value="3"/>
	  <distance name="bottom_height" value="3"/>
	  <distance name="left_titlebar_edge" value="2"/>
	  <distance name="right_titlebar_edge" value="5"/>
	  <distance name="title_vertical_pad" value="5"/>
	  <border name="title_border" left="2" right="5" top="1" bottom="0"/>
	  <border name="button_border" left="0" right="0" top="1" bottom="0"/>
	  <distance name="button_width" value="26"/>
	  <distance name="button_height" value="20"/>
	</frame_geometry>

	<frame_geometry name="utility" title_scale="small">
	  <distance name="left_width" value="3"/>
	  <distance name="right_width" value="3"/>
	  <distance name="bottom_height" value="3"/>
	  <distance name="left_titlebar_edge" value="2"/>
	  <distance name="right_titlebar_edge" value="5"/>
	  <distance name="title_vertical_pad" value="0"/>
	  <border name="title_border" left="2" right="5" top="1" bottom="0"/>
	  <border name="button_border" left="0" right="0" top="1" bottom="1"/>
	  <distance name="button_width" value="22"/>
	  <distance name="button_height" value="16"/>
	</frame_geometry>

	<frame_geometry name="border" has_title="false">
	  <distance name="left_width" value="3"/>
	  <distance name="right_width" value="3"/>
	  <distance name="bottom_height" value="3"/>
	  <distance name="left_titlebar_edge" value="0"/>
	  <distance name="right_titlebar_edge" value="0"/>
	  <distance name="button_width" value="0"/>
	  <distance name="button_height" value="0"/>
	  <distance name="title_vertical_pad" value="3"/>
	  <border name="title_border" left="0" right="0" top="0" bottom="0"/>
	  <border name="button_border" left="0" right="0" top="0" bottom="0"/>
	</frame_geometry>

	<frame_geometry name="maximized" title_scale="medium">
	  <distance name="left_width" value="0"/>
	  <distance name="right_width" value="0"/>
	  <distance name="bottom_height" value="0"/>
	  <distance name="left_titlebar_edge" value="0"/>
	  <distance name="right_titlebar_edge" value="0"/>
	  <distance name="title_vertical_pad" value="5"/>
	  <border name="title_border" left="2" right="5" top="1" bottom="0"/>
	  <border name="button_border" left="0" right="0" top="1" bottom="0"/>
	  <distance name="button_width" value="26"/>
	  <distance name="button_height" value="20"/>
	</frame_geometry>

	<frame_geometry name="maximized_shaded" title_scale="medium">
	  <distance name="left_width" value="0"/>
	  <distance name="right_width" value="0"/>
	  <distance name="bottom_height" value="0"/>
	  <distance name="left_titlebar_edge" value="0"/>
	  <distance name="right_titlebar_edge" value="0"/>
	  <distance name="title_vertical_pad" value="5"/>
	  <border name="title_border" left="2" right="5" top="1" bottom="0"/>
	  <border name="button_border" left="0" right="0" top="1" bottom="0"/>
	  <distance name="button_width" value="26"/>
	  <distance name="button_height" value="20"/>
	</frame_geometry>

	<!-- Titlebar -->
	<draw_ops name="bg_active">
		<gradient type="vertical" x="0" y="0" width="width" height="height / 2">
			<color value="blend/white/black/0.7"/>
			<color value="blend/white/black/1.0"/>
		</gradient>
		<gradient type="vertical" x="0" y="height / 2" width="width" height="height / 2">
			<color value="shade/black/0.95"/>
			<color value="blend/white/black/0.9"/>
		</gradient>
		 <line color="blend/white/black/0.4" width="1" x1="0" y1="0" x2="width" y2="0"/>
		<line color="blend/black/black/0.8" width="1" x1="0" y1="height - 1" x2="width" y2="height - 1"/>
	</draw_ops>

	<draw_ops name="bg_active-i">
		<gradient type="vertical" x="0" y="0" width="width" height="height / 2">
			<color value="blend/white/black/0.7"/>
			<color value="blend/white/black/1.0"/>
		</gradient>
		<gradient type="vertical" x="0" y="height / 2" width="width" height="height / 2">
			<color value="shade/black/0.95"/>
			<color value="blend/black/black/1.0"/>
		</gradient>
		 <line color="blend/white/black/0.4" width="1" x1="0" y1="0" x2="width" y2="0"/>
		<line color="blend/black/black/0.8" width="1" x1="0" y1="height - 1" x2="width" y2="height - 1"/>
	</draw_ops>

	<draw_ops name="bg_active_shaded">
		<gradient type="vertical" x="0" y="0" width="width" height="height / 2">
			<color value="blend/white/black/0.7"/>
			<color value="blend/white/black/1.0"/>
		</gradient>
		<gradient type="vertical" x="0" y="height / 2" width="width" height="height / 2">
			<color value="shade/black/0.95"/>
			<color value="blend/white/black/0.9"/>
		</gradient>
		 <line color="blend/white/black/0.4" width="1" x1="0" y1="0" x2="width" y2="0"/>
		<line color="blend/white/black/0.4" width="1" x1="0" y1="height - 2" x2="width" y2="height - 2"/>
		<line color="blend/black/black/0.4" width="1" x1="0" y1="height - 1" x2="width" y2="height - 1"/>
	</draw_ops>

	<draw_ops name="bg_active-i_shaded">
		<gradient type="vertical" x="0" y="0" width="width" height="height / 2">
			<color value="blend/white/black/0.7"/>
			<color value="blend/white/black/1.0"/>
		</gradient>
		<gradient type="vertical" x="0" y="height / 2" width="width" height="height / 2">
			<color value="shade/black/0.95"/>
			<color value="blend/black/black/1.0"/>
		</gradient>
		 <line color="blend/white/black/0.4" width="1" x1="0" y1="0" x2="width" y2="0"/>
		<line color="blend/white/black/0.4" width="1" x1="0" y1="height - 2" x2="width" y2="height - 2"/>
		<line color="blend/black/black/0.7" width="1" x1="0" y1="height - 1" x2="width" y2="height - 1"/>
	</draw_ops>
	<!-- End Titlebar -->

	<!-- buttons -->
	<draw_ops name="minimize_button_normal">
	  <image filename="minimize.png" colorize="blend/black/black/0.95" 
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="minimize_button_normal_shaded">
	  <image filename="minimize.png" colorize="blend/black/black/0.95" 
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="minimize_button_normal_prelight">
	  <image filename="minimize-pre.png" colorize="blend/black/black/0.95" 
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="minimize_button_normal_shaded_prelight">
	  <image filename="minimize-pre.png" colorize="blend/black/black/0.95" 
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="minimize_button_pressed">
	  <image filename="minimize-inv.png" colorize="blend/black/black/0.85" 
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="minimize_button_pressed_shaded">
	  <image filename="minimize-inv.png" colorize="blend/black/black/0.85" 
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="minimize_button-i">
	  <image filename="minimize-i.png" colorize="shade/black/0.9"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="minimize_button-i_shaded">
	  <image filename="minimize-i.png" colorize="shade/black/0.9"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="maximize_button_normal">
	  <image filename="maximize.png" colorize="blend/black/black/0.95"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="maximize_button_normal_shaded">
	  <image filename="maximize.png" colorize="blend/black/black/0.95" 
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="maximize_button_normal_prelight">
	  <image filename="maximize-pre.png" colorize="blend/black/black/0.95"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="maximize_button_normal_shaded_prelight">
	  <image filename="maximize-pre.png" colorize="blend/black/black/0.95" 
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="maximize_button_pressed">
	  <image filename="maximize-inv.png" colorize="blend/black/black/0.85"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="maximize_button_pressed_shaded">
	  <image filename="maximize-inv.png" colorize="blend/black/black/0.85"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="maximize_button-i">
	  <image filename="maximize-i.png" colorize="shade/black/0.9"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="maximize_button-i_shaded">
	  <image filename="maximize-i.png" colorize="shade/black/0.9"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="restore_button_normal">
	  <image filename="restore.png" colorize="blend/black/black/0.95"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="restore_button_normal_shaded">
	  <image filename="restore.png" colorize="blend/black/black/0.95" 
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="restore_button_normal_prelight">
	  <image filename="restore-pre.png" colorize="blend/black/black/0.95"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="restore_button_normal_shaded_prelight">
	  <image filename="restore-pre.png" colorize="blend/black/black/0.95" 
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="restore_button_pressed">
	  <image filename="restore-inv.png" colorize="blend/black/black/0.85"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="restore_button_pressed_shaded">
	  <image filename="restore-inv.png" colorize="blend/black/black/0.85"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="restore_button-i">
	  <image filename="restore-i.png" colorize="shade/black/0.9"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="restore_button-i_shaded">
	  <image filename="restore-i.png" colorize="shade/black/0.9"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="close_button_normal">
	  <image filename="close.png" x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="close_button_normal_shaded">
	  <image filename="close.png" colorize="blend/black/black/0.95" 
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="close_button_normal_prelight">
	  <image filename="close-pre.png"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="close_button_normal_shaded_prelight">
	  <image filename="close-pre.png" colorize="blend/black/black/0.95" 
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="close_button_pressed">
	  <image filename="close-inv.png"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="close_button_pressed_shaded">
	  <image filename="close-inv.png"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="close_button-i">
	  <image filename="close-i.png" colorize="shade/black/0.9"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>

	<draw_ops name="close_button-i_shaded">
	  <image filename="close-i.png" colorize="shade/black/0.9"
			x="0" y="0" width="26" height="20"/>
	</draw_ops>



	<draw_ops name="close_button_normal-u">
	  <image filename="close.png" x="0" y="0" width="22" height="16"/>
	</draw_ops>

	<draw_ops name="close_button_normal_shaded-u">
	  <image filename="close.png" colorize="blend/black/black/0.95" 
			x="0" y="0" width="22" height="16"/>
	</draw_ops>

	<draw_ops name="close_button_normal_prelight-u">
	  <image filename="close-pre.png"
			x="0" y="0" width="22" height="16"/>
	</draw_ops>

	<draw_ops name="close_button_normal_shaded_prelight-u">
	  <image filename="close-pre.png" colorize="blend/black/black/0.95" 
			x="0" y="0" width="22" height="16"/>
	</draw_ops>

	<draw_ops name="close_button_pressed-u">
	  <image filename="close-inv.png"
			x="0" y="0" width="22" height="16"/>
	</draw_ops>

	<draw_ops name="close_button_pressed_shaded-u">
	  <image filename="close-inv.png"
			x="0" y="0" width="22" height="16"/>
	</draw_ops>

	<draw_ops name="close_button-i-u">
	  <image filename="close-i.png" colorize="shade/black/0.9"
			x="0" y="0" width="22" height="16"/>
	</draw_ops>

	<draw_ops name="close_button-i_shaded-u">
	  <image filename="close-i.png" colorize="shade/black/0.9"
			x="0" y="0" width="22" height="16"/>
	</draw_ops>





	<draw_ops name="menu_button_normal">
	  <icon alpha="1.0" x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
	</draw_ops>

	<draw_ops name="menu_button_normal_shaded">
	  <icon alpha="1.0" x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
	</draw_ops>

	<draw_ops name="menu_button_normal_prelight">
	  <icon alpha="0.7" x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
	</draw_ops>

	<draw_ops name="menu_button_normal_shaded_prelight">
	  <icon alpha="0.7" x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
	</draw_ops>

	<draw_ops name="menu_button_pressed">
	  <icon alpha="0.5" x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
	</draw_ops>

	<draw_ops name="menu_button-i">
	  <icon alpha="0.50" x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
	</draw_ops>

	<draw_ops name="menu_button-i_shaded">
	  <icon alpha="0.50" x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
	</draw_ops>
	<!-- end of buttons -->

	<!-- Left and Right Titlbar -->
	<draw_ops name="left_titlebar_edge">
		<gradient type="vertical" x="1" y="0" width="width" height="height / 2">
			<color value="blend/white/black/0.4"/>
			<color value="blend/white/black/0.6"/>
		</gradient>
		<gradient type="vertical" x="1" y="height / 2" width="width" height="height / 2">
			<color value="blend/white/black/0.5"/>
			<color value="blend/white/black/0.4"/>
		</gradient>
	</draw_ops>

	<draw_ops name="left_titlebar_edge_shaded">
		<gradient type="vertical" x="1" y="0" width="width" height="height / 2">
			<color value="blend/white/black/0.4"/>
			<color value="blend/white/black/0.6"/>
		</gradient>
		<gradient type="vertical" x="1" y="height / 2" width="width" height="height / 2">
			<color value="blend/white/black/0.5"/>
			<color value="blend/white/black/0.4"/>
		</gradient>
		<line color="blend/black/black/0.4" width="1" x1="0" y1="height - 1" x2="width" y2="height - 1"/>
	</draw_ops>

	<draw_ops name="right_titlebar_edge">
		<gradient type="vertical" x="0" y="0" width="width" height="height / 2">
			<color value="blend/white/black/0.4"/>
			<color value="blend/white/black/0.6"/>
		</gradient>
		<gradient type="vertical" x="0" y="height / 2" width="width" height="height / 2">
			<color value="blend/white/black/0.5"/>
			<color value="blend/white/black/0.4"/>
		</gradient>
		<gradient type="vertical" x="0" y="0" width="3" height="height / 2">
			<color value="blend/white/black/0.7"/>
			<color value="blend/white/black/1.0"/>
		</gradient>
		<gradient type="vertical" x="0" y="height / 2" width="3" height="height / 2">
			<color value="shade/black/0.95"/>
			<color value="blend/white/black/0.9"/>
		</gradient>
		 <line color="blend/white/black/0.4" width="1" x1="0" y1="0" x2="width" y2="0"/>
		<line color="blend/black/black/0.8" width="1" x1="0" y1="height - 1" x2="3" y2="height - 1"/>
	  <rectangle color="blend/black/black/0.4" filled="false" x="4" y="0" width="width-1" height="height-1"/>
	</draw_ops>

	<draw_ops name="right_titlebar_edge_shaded">
		<gradient type="vertical" x="0" y="0" width="width" height="height / 2">
			<color value="blend/white/black/0.4"/>
			<color value="blend/white/black/0.6"/>
		</gradient>
		<gradient type="vertical" x="0" y="height / 2" width="width" height="height / 2">
			<color value="blend/white/black/0.5"/>
			<color value="blend/white/black/0.4"/>
		</gradient>
		<gradient type="vertical" x="0" y="0" width="3" height="height / 2">
			<color value="blend/white/black/0.7"/>
			<color value="blend/white/black/1.0"/>
		</gradient>
		<gradient type="vertical" x="0" y="height / 2" width="3" height="height / 2">
			<color value="shade/black/0.95"/>
			<color value="blend/white/black/0.9"/>
		</gradient>
		 <line color="blend/white/black/0.4" width="1" x1="0" y1="0" x2="width" y2="0"/>
		<line color="blend/white/black/0.4" width="1" x1="0" y1="height - 2" x2="width" y2="height - 2"/>
		<line color="blend/black/black/0.4" width="1" x1="0" y1="height - 1" x2="width" y2="height - 1"/>
	  <rectangle color="blend/black/black/0.4" filled="false" x="4" y="0" width="width-1" height="height-1"/>
	</draw_ops>

	<draw_ops name="right_titlebar_edge-i">
		<gradient type="vertical" x="0" y="0" width="width" height="height / 2">
			<color value="blend/white/black/0.4"/>
			<color value="blend/white/black/0.4"/>
		</gradient>
		<gradient type="vertical" x="0" y="height / 2" width="width" height="height / 2">
			<color value="blend/white/black/0.4"/>
			<color value="blend/white/black/0.4"/>
		</gradient>
		<gradient type="vertical" x="0" y="0" width="width" height="height / 2">
			<color value="blend/white/black/0.7"/>
			<color value="blend/white/black/1.0"/>
		</gradient>
		<gradient type="vertical" x="0" y="height / 2" width="width" height="height / 2">
			<color value="shade/black/0.95"/>
			<color value="blend/black/black/1.0"/>
		</gradient>
		 <line color="blend/white/black/0.4" width="1" x1="0" y1="0" x2="width" y2="0"/>
		<line color="blend/black/black/0.8" width="1" x1="0" y1="height - 1" x2="3" y2="height - 1"/>
	  <rectangle color="blend/white/black/0.4" filled="false" x="3" y="0" width="width-1" height="height-1"/>
	  <rectangle color="blend/black/black/0.7" filled="false" x="4" y="0" width="width-1" height="height-1"/>
	</draw_ops>

	<draw_ops name="right_titlebar_edge-i_shaded">
		<gradient type="vertical" x="0" y="0" width="width" height="height / 2">
			<color value="blend/white/black/0.4"/>
			<color value="blend/white/black/0.4"/>
		</gradient>
		<gradient type="vertical" x="0" y="height / 2" width="width" height="height / 2">
			<color value="blend/white/black/0.4"/>
			<color value="blend/white/black/0.4"/>
		</gradient>
		<gradient type="vertical" x="0" y="0" width="3" height="height / 2">
			<color value="blend/white/black/0.7"/>
			<color value="blend/white/black/1.0"/>
		</gradient>
		<gradient type="vertical" x="0" y="height / 2" width="3" height="height / 2">
			<color value="shade/black/0.95"/>
			<color value="blend/black/black/1.0"/>
		</gradient>
		 <line color="blend/white/black/0.4" width="1" x1="0" y1="0" x2="width" y2="0"/>
		<line color="blend/white/black/0.4" width="1" x1="0" y1="height - 2" x2="width" y2="height - 2"/>
		<line color="blend/black/black/0.7" width="1" x1="0" y1="height - 1" x2="width" y2="height - 1"/>
	  <rectangle color="blend/black/black/0.7" filled="false" x="4" y="0" width="width-1" height="height-1"/>
	</draw_ops>
	<!-- End Left and Right Titlbar -->

	<draw_ops name="title_bg">
	  <include name="bg_active"/>
	</draw_ops>

	<draw_ops name="title_bg-i">
	  <include name="bg_active-i"/>
	</draw_ops>

	<draw_ops name="title_bg_shaded">
	  <include name="bg_active_shaded"/>
	</draw_ops>

	<draw_ops name="title_bg-i_shaded">
	  <include name="bg_active-i_shaded"/>
	</draw_ops>

	<draw_ops name="title_focused">
 		 <!--<title color="shade/black/0.3" x="5 `max` (width-title_width)/2+1" y="1 `max` ((height-title_height)/2)+1"/>-->
		
  		 <title color="blend/black/black/0.8" x="4 `max` (width-title_width)/2-1" y="0 `max` ((height-title_height)/2)+1"/>
  		 <title color="blend/black/black/0.9" x="4 `max` (width-title_width)/2+1" y="0 `max` ((height-title_height)/2)-1"/>
  		 <title color="blend/black/black/0.9" x="4 `max` (width-title_width)/2-1" y="0 `max` ((height-title_height)/2)-1"/>
  		 <title color="blend/black/black/0.5" x="4 `max` (width-title_width)/2+1" y="0 `max` ((height-title_height)/2)+1"/>
  		 <title color="blend/black/black/0.7" x="(4 `max` (width-title_width)) / 2 + 2" y="(((height - title_height) / 2) `max` 0) + 2"/>
  		<title color="#ffffff" x="4 `max` (width-title_width)/2" y="0 `max` ((height-title_height)/2)"/>
	</draw_ops>

	<draw_ops name="title_unfocused">
  		<title color="shade/black/1.1" x="5 `max` (width-title_width)/2+1" y="1 `max` ((height-title_height)/2)+1"/>
  		<title color="shade/black/0.7" x="4 `max` (width-title_width)/2" y="0 `max` ((height-title_height)/2)"/>
	</draw_ops>

	<draw_ops name="title_focused_shaded">
 		 <!--<title color="shade/black/0.3" x="5 `max` (width-title_width)/2+1" y="1 `max` ((height-title_height)/2)+1"/>-->
  		 <title color="blend/black/black/0.8" x="4 `max` (width-title_width)/2-1" y="0 `max` ((height-title_height)/2)+1"/>
  		 <title color="blend/black/black/0.9" x="4 `max` (width-title_width)/2+1" y="0 `max` ((height-title_height)/2)-1"/>
  		 <title color="blend/black/black/0.9" x="4 `max` (width-title_width)/2-1" y="0 `max` ((height-title_height)/2)-1"/>
  		 <title color="blend/black/black/0.5" x="4 `max` (width-title_width)/2+1" y="0 `max` ((height-title_height)/2)+1"/>
  		 <title color="blend/black/black/0.7" x="(4 `max` (width-title_width)) / 2 + 2" y="(((height - title_height) / 2) `max` 0) + 2"/>
  		<title color="#ffffff" x="4 `max` (width-title_width)/2" y="0 `max` ((height-title_height)/2)"/>
	</draw_ops>

	<draw_ops name="title_unfocused_shaded">
  		<title color="shade/black/1.1" x="5 `max` (width-title_width)/2+1" y="1 `max` ((height-title_height)/2)+1"/>
  		<title color="shade/black/0.7" x="4 `max` (width-title_width)/2" y="0 `max` ((height-title_height)/2)"/>
	</draw_ops>

	<draw_ops name="outer_bevel_focused">
	  <rectangle color="blend/black/black/0.8" filled="true" x="0" y="0" width="width" height="height"/>
	  <rectangle color="blend/white/black/0.4" filled="false" x="1" y="1" width="width -2" height="height -2"/>
	  <rectangle color="blend/white/black/0.4" filled="false" x="0" y="0" width="width-2" height="height-2"/>
	  <rectangle color="blend/black/black/0.4" filled="false" x="0" y="0" width="width-1" height="height-1"/>
	</draw_ops>

	<draw_ops name="outer_bevel_unfocused">
	  <rectangle color="blend/black/black/0.7" filled="true" x="0" y="0" width="width" height="height"/>
	  <rectangle color="blend/white/black/0.5" filled="false" x="1" y="1" width="width -2" height="height -2"/>
	  <rectangle color="blend/white/black/0.5" filled="false" x="0" y="0" width="width-2" height="height-2"/>
	  <rectangle color="blend/black/black/0.7" filled="false" x="0" y="0" width="width-1" height="height-1"/>
	</draw_ops>

	<draw_ops name="blank">
	<!-- nothing -->
	</draw_ops>

	<frame_style name="normal_unfocused" geometry="normal">
	  <piece position="entire_background" draw_ops="outer_bevel_unfocused"/>
	  <piece position="titlebar_middle" draw_ops="title_bg-i"/>
	  <piece position="title" draw_ops="title_unfocused"/>
   	  <piece position="right_titlebar_edge" draw_ops="right_titlebar_edge-i"/>
	  <button function="close" state="normal" draw_ops="close_button-i"/>
	  <button function="close" state="pressed" draw_ops="close_button_pressed"/>
	  <button function="minimize" state="normal" draw_ops="minimize_button-i"/>
	  <button function="minimize" state="pressed" draw_ops="minimize_button_pressed"/>
	  <button function="maximize" state="normal" draw_ops="maximize_button-i"/>
	  <button function="maximize" state="pressed" draw_ops="maximize_button_pressed"/>
	  <button function="menu" state="normal" draw_ops="menu_button-i"/>
	  <button function="menu" state="pressed" draw_ops="menu_button_pressed"/>
	</frame_style>

	<frame_style name="normal_focused" geometry="normal">
	  <piece position="entire_background" draw_ops="outer_bevel_focused"/>
	  <piece position="titlebar_middle" draw_ops="title_bg"/>
	  <piece position="title" draw_ops="title_focused"/>
   	  <piece position="left_titlebar_edge" draw_ops="left_titlebar_edge"/>
   	  <piece position="right_titlebar_edge" draw_ops="right_titlebar_edge"/>
	  <button function="close" state="normal" draw_ops="close_button_normal"/>
	  <button function="close" state="prelight" draw_ops="close_button_normal_prelight"/>
	  <button function="close" state="pressed" draw_ops="close_button_pressed"/>
	  <button function="minimize" state="normal" draw_ops="minimize_button_normal"/>
	  <button function="minimize" state="prelight" draw_ops="minimize_button_normal_prelight"/>
	  <button function="minimize" state="pressed" draw_ops="minimize_button_pressed"/>
	  <button function="maximize" state="normal" draw_ops="maximize_button_normal"/>
	  <button function="maximize" state="prelight" draw_ops="maximize_button_normal_prelight"/>
	  <button function="maximize" state="pressed" draw_ops="maximize_button_pressed"/>
	  <button function="menu" state="normal" draw_ops="menu_button_normal"/>
	  <button function="menu" state="prelight" draw_ops="menu_button_normal_prelight"/>
	  <button function="menu" state="pressed" draw_ops="menu_button_pressed"/>
	</frame_style>

	<frame_style name="normal_unfocused_maximized" geometry="maximized" parent="normal_unfocused">
	  <piece position="entire_background" draw_ops="outer_bevel_unfocused"/>
	  <piece position="title" draw_ops="title_unfocused"/>
	  <button function="maximize" state="normal" draw_ops="restore_button-i"/>
	  <button function="maximize" state="pressed" draw_ops="restore_button_pressed"/>
	</frame_style>

	<frame_style name="normal_focused_maximized" geometry="maximized" parent="normal_focused">
	  <piece position="entire_background" draw_ops="outer_bevel_focused"/>
	  <piece position="title" draw_ops="title_focused"/>
	  <button function="maximize" state="normal" draw_ops="restore_button_normal"/>
	  <button function="maximize" state="prelight" draw_ops="restore_button_normal_prelight"/>
	  <button function="maximize" state="pressed" draw_ops="restore_button_pressed"/>
	</frame_style>

	<frame_style name="normal_unfocused_shaded" geometry="shaded">
	  <piece position="entire_background" draw_ops="outer_bevel_unfocused"/>
	  <piece position="titlebar_middle" draw_ops="title_bg-i_shaded"/>
	  <piece position="title" draw_ops="title_unfocused_shaded"/>
   	  <piece position="right_titlebar_edge" draw_ops="right_titlebar_edge-i_shaded"/>
	  <button function="close" state="normal" draw_ops="close_button-i_shaded"/>
	  <button function="close" state="pressed" draw_ops="close_button_pressed"/>
	  <button function="minimize" state="normal" draw_ops="minimize_button-i_shaded"/>
	  <button function="minimize" state="pressed" draw_ops="minimize_button_pressed"/>
	  <button function="maximize" state="normal" draw_ops="maximize_button-i_shaded"/>
	  <button function="maximize" state="pressed" draw_ops="maximize_button_pressed"/>
	  <button function="menu" state="normal" draw_ops="menu_button-i_shaded"/>
	  <button function="menu" state="pressed" draw_ops="menu_button_pressed"/>
	</frame_style>

	<frame_style name="normal_focused_shaded" geometry="shaded">
	  <piece position="entire_background" draw_ops="outer_bevel_focused"/>
	  <piece position="titlebar_middle" draw_ops="title_bg_shaded"/>
	  <piece position="title" draw_ops="title_focused_shaded"/>
   	  <piece position="left_titlebar_edge" draw_ops="left_titlebar_edge_shaded"/>
   	  <piece position="right_titlebar_edge" draw_ops="right_titlebar_edge_shaded"/>
	  <button function="close" state="normal" draw_ops="close_button_normal_shaded"/>
	  <button function="close" state="prelight" draw_ops="close_button_normal_shaded_prelight"/>
	  <button function="close" state="pressed" draw_ops="close_button_pressed_shaded"/>
	  <button function="minimize" state="normal" draw_ops="minimize_button_normal_shaded"/>
	  <button function="minimize" state="prelight" draw_ops="minimize_button_normal_shaded_prelight"/>
	  <button function="minimize" state="pressed" draw_ops="minimize_button_pressed_shaded"/>
	  <button function="maximize" state="normal" draw_ops="maximize_button_normal_shaded"/>
	  <button function="maximize" state="prelight" draw_ops="maximize_button_normal_shaded_prelight"/>
	  <button function="maximize" state="pressed" draw_ops="maximize_button_pressed_shaded"/>
	  <button function="menu" state="normal" draw_ops="menu_button_normal_shaded"/>
	  <button function="menu" state="prelight" draw_ops="menu_button_normal_shaded_prelight"/>
	  <button function="menu" state="pressed" draw_ops="menu_button_pressed"/>
	</frame_style>

	<frame_style name="normal_unfocused_maximized_shaded" geometry="maximized" parent="normal_unfocused_shaded">
	  <button function="maximize" state="normal" draw_ops="restore_button-i_shaded"/>
	</frame_style>

	<frame_style name="normal_focused_maximized_shaded" geometry="maximized" parent="normal_focused_shaded">
	  <button function="maximize" state="normal" draw_ops="restore_button_normal_shaded"/>
	  <button function="maximize" state="prelight" draw_ops="restore_button_normal_shaded_prelight"/>
	  <button function="maximize" state="pressed" draw_ops="restore_button_pressed_shaded"/>
	</frame_style>

	<frame_style name="utility_unfocused" geometry="utility" parent="normal_unfocused">
	  <piece position="title" draw_ops="title_unfocused"/>
	  <button function="close" state="normal" draw_ops="close_button-i-u"/>
	  <button function="close" state="pressed" draw_ops="close_button_pressed-u"/>
	</frame_style>

	<frame_style name="utility_focused" geometry="utility" parent="normal_focused">
	  <piece position="title" draw_ops="title_focused"/>
	  <button function="close" state="normal" draw_ops="close_button_normal-u"/>
	  <button function="close" state="prelight" draw_ops="close_button_normal_prelight-u"/>
	  <button function="close" state="pressed" draw_ops="close_button_pressed-u"/>
	</frame_style>

	<frame_style name="utility_unfocused_shaded" geometry="utility" parent="normal_unfocused_shaded">
	  <piece position="title" draw_ops="title_unfocused"/>
	  <button function="close" state="normal" draw_ops="close_button-i_shaded-u"/>
	  <button function="close" state="pressed" draw_ops="close_button_pressed-u"/>
	</frame_style>

	<frame_style name="utility_focused_shaded" geometry="utility" parent="normal_focused_shaded">
	  <piece position="title" draw_ops="title_focused"/>
	  <button function="close" state="normal" draw_ops="close_button_normal_shaded-u"/>
	  <button function="close" state="prelight" draw_ops="close_button_normal_shaded_prelight-u"/>
	  <button function="close" state="pressed" draw_ops="close_button_pressed_shaded-u"/>
	</frame_style>

	<frame_style name="border" geometry="border" parent="normal_focused">
	  <piece position="entire_background" draw_ops="outer_bevel_focused"/>
	  <piece position="titlebar_middle" draw_ops="blank"/>
	  <piece position="title" draw_ops="blank"/>
	</frame_style>

	<frame_style_set name="normal">
		<frame focus="yes" state="normal" resize="both" style="normal_focused"/>
		<frame focus="no" state="normal" resize="both" style="normal_unfocused"/>
		<frame focus="yes" state="maximized" style="normal_focused_maximized"/>
		<frame focus="no" state="maximized" style="normal_unfocused_maximized"/>
		<frame focus="yes" state="shaded" style="normal_focused_shaded"/>
		<frame focus="no" state="shaded" style="normal_unfocused_shaded"/>
		<frame focus="yes" state="maximized_and_shaded" style="normal_focused_maximized_shaded"/>
		<frame focus="no" state="maximized_and_shaded" style="normal_unfocused_maximized_shaded"/>
	</frame_style_set>

	<frame_style_set name="utility" parent="normal">
		<frame focus="yes" state="normal" resize="both" style="utility_focused"/>
		<frame focus="no" state="normal" resize="both" style="utility_unfocused"/>
		<frame focus="yes" state="maximized" style="utility_focused"/>
		<frame focus="no" state="maximized" style="utility_unfocused"/>
		<frame focus="yes" state="shaded" style="utility_focused_shaded"/>
		<frame focus="no" state="shaded" style="utility_unfocused_shaded"/>
		<frame focus="yes" state="maximized_and_shaded" style="utility_focused"/>
		<frame focus="no" state="maximized_and_shaded" style="utility_unfocused"/>
	</frame_style_set>

	<frame_style_set name="border">
		<frame focus="yes" state="normal" resize="both" style="border"/>
		<frame focus="no" state="normal" resize="both" style="border"/>
		<frame focus="yes" state="maximized" style="border"/>
		<frame focus="no" state="maximized" style="border"/>
		<frame focus="yes" state="shaded" style="border"/>
		<frame focus="no" state="shaded" style="border"/>
		<frame focus="yes" state="maximized_and_shaded" style="border"/>
		<frame focus="no" state="maximized_and_shaded" style="border"/>
	</frame_style_set>

	<window type="normal" style_set="normal"/>
	<window type="dialog" style_set="normal"/>
	<window type="modal_dialog" style_set="normal"/>
	<window type="menu" style_set="normal"/>
	<window type="utility" style_set="utility"/>
	<window type="border" style_set="border"/>

	<menu_icon function="close" state="normal" draw_ops="close_button_normal"/>
	<menu_icon function="maximize" state="normal" draw_ops="maximize_button_normal"/>
	<menu_icon function="unmaximize" state="normal" draw_ops="maximize_button_normal"/>
	<menu_icon function="minimize" state="normal" draw_ops="minimize_button_normal"/>

</metacity_theme>

---

### Post by dumblebee100 on 2009-09-15
sorry for the late reply ..

I got time today 

I inspected your metacity theme ..I added it to my custom theme ..but my theme is not detecting it ...so I could not test it on my system 

but after inspection .I could find one thing 

just check these sections by trial and error methods 
just remove the default colour and keep some black or white then see the results ..if you found some change to your required elements then keep your preferred colour 

<draw_ops name="title_focused">
<draw_ops name="title_unfocused">
<draw_ops name="title_focused_shaded">
<draw_ops name="title_unfocused_shaded">
<draw_ops name="outer_bevel_unfocused">
<draw_ops name="outer_bevel_focused">


edit the colours like this .
suppose a line is like this
```
<title color="blend/black/black/0.8" x="4 `max` (width-title_width)/2-1" y="0 `max` ((height-title_height)/2)+1"/>
```

then change it to something like this 
```
<title color="#000000" x="4 `max` (width-title_width)/2-1" y="0 `max` ((height-title_height)/2)+1"/>
```

here #000000 is for black ...if you want other colours in this hexa format then install gcolor2

---

