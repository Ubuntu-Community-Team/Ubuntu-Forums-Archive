---
title: "Metacity titlebar text allignment"
date: 2009-04-28
forum: General Help
---

### Post by Jameshardy88 on 2009-04-28
Hi, im trying to customise a theme to get it to a format that i like. Im currently trying to edit the metacity theme so that the text in the titlebar will be alligned ideally to the left, although centered would not be too bad. It is currently alligned to the right and as such seems to frequently cut off text. I have tried to edit it myself but have not found out exaclty how to do it and would appreciate any help,

Thanks

```

<?xml version="1.0"?>
<metacity_theme>
<info>
  <name>Macchiato</name>
  <author>Ryan Johnson</author>
  <copyright>Copyright 2008, Ryan Johnson</copyright>
  <date>February 15, 2009</date>
  <description>(v1.0) Metacity port of the Macchiato Emerald Theme by SpecKtacle.</description>
</info>

<!-- define constants -->
<constant name="ArrowWidth" value="7"/>
<constant name="ArrowHeight" value="5"/>
<constant name="ButtonIPad" value="3"/>
<constant name="ThickLineWidth" value="3"/>
<constant name="IconTitleSpacing" value="2"/>
<constant name="SpacerWidth" value="7"/>
<constant name="SpacerHeight" value="11"/>

<!-- Maximum Button Width/Height -->
<!-- V2
<constant name="ActiveColor" value="#E2EEC8" />
<constant name="InactiveColor" value="#D3CAAA" />
-->

<frame_geometry name="normal"
  rounded_top_left="true"
  rounded_top_right="false"
  rounded_bottom_left="false"
  rounded_bottom_right="false"
>
  <distance name="left_width"           value="4"/>
  <distance name="right_width"          value="4"/>
  <distance name="bottom_height"        value="4"/>
  <distance name="left_titlebar_edge"   value="14"/>
  <distance name="right_titlebar_edge"  value="4"/>

  <distance name="button_width"   value="16" />
  <distance name="button_height"  value="16" />

  <distance name="title_vertical_pad" value="2"/>
  <border name="title_border" left="2" right="2" top="3" bottom="3"/>
  
  <!-- Can I get the buttons to overlap? -->
  <border name="button_border" left="0" right="0" top="2" bottom="2"/>
</frame_geometry>
<frame_geometry name="normal_small_borders"         parent="normal">
  <distance name="left_width"           value="2"/>
  <distance name="right_width"          value="2"/>
  <distance name="bottom_height"        value="2"/>
  <distance name="left_titlebar_edge"   value="2"/>
  <distance name="right_titlebar_edge"  value="2"/>
  
  <distance name="title_vertical_pad" value="2" />
  <border name="title_border"   left="2" right="2" top="1" bottom="1"/>
  <border name="button_border"  left="0" right="0" top="1" bottom="1"/>
</frame_geometry>
<frame_geometry name="utility" title_scale="small"  parent="normal"
  rounded_top_left="true"
  rounded_top_right="false"
  rounded_bottom_left="false"
  rounded_bottom_right="false"
>
  <distance name="left_width"           value="2"/>
  <distance name="right_width"          value="2"/>
  <distance name="bottom_height"        value="2" />
  <distance name="left_titlebar_edge"   value="2" />
  <distance name="right_titlebar_edge"  value="2" />

  <distance name="title_vertical_pad" value="2"/>
  <border name="title_border" left="2" right="2" top="2" bottom="2"/>
</frame_geometry>
<frame_geometry name="frame_maximized"              parent="normal"
  rounded_top_left="false"
  rounded_top_right="false"
  rounded_bottom_left="false"
  rounded_bottom_right="false"
>
  <distance name="left_width"     value="0"/>
  <distance name="right_width"    value="0"/>
  <distance name="bottom_height"  value="0"/>
</frame_geometry>
<frame_geometry name="frame_square"                parent="normal"
  rounded_top_left="false"
  rounded_top_right="false"
  rounded_bottom_left="false"
  rounded_bottom_right="false"
>
<!-- No Change but Corners -->
</frame_geometry>

<!-- WINDOW BG COLOR -->
<draw_ops name="mocha_bg">
  <rectangle      color="#373330" filled="true"
    x="0"         y="0"
    width="width" height="height"/>
</draw_ops>


<draw_ops name="title_hilight_active">
<!-- ATTEMPT AT ROUND HIGHLIGHT/GLOW -->
  <image filename="pix/white_glow_half_round.png" x="0-10" y="1" width="width+20" height="12" alpha="0.08" />
</draw_ops>
<draw_ops name="title_hilight_inactive">
  <!-- NO GLOW -->
</draw_ops>

<draw_ops name="blank">
  <!-- nothing -->
</draw_ops>

<!-- 1px stroke around window --><!-- DONE -->
<draw_ops name="tl_round_overlay_active">
<!-- TOP LEFT ROUND -->
<!-- Default Corner Radius -->
  <line x1="3" x2="4" y1="1" y2="1" color="#E2EEC8" />
  <line x1="2" x2="2" y1="2" y2="2" color="#E2EEC8" />
  <line x1="1" x2="1" y1="3" y2="4" color="#E2EEC8" />

<!-- 20 Radius -->
<!-- V2
  <image filename="pix/tlcorner_active.png" x="1" y="1" width="21" height="21" alpha="1.0" />
-->
</draw_ops>
<draw_ops name="square_overlay_active">
<!-- LEFT LINE -->
  <line x1="0" y1="0" x2="0" y2="height" color="#E2EEC8" />
<!-- TOP LINE -->
  <line x1="1" y1="0" x2="width-1" y2="0" color="#E2EEC8" />
<!-- RIGHT LINE -->
  <line x1="width-1" y1="1" x2="width-1" y2="height" color="#E2EEC8" />
<!-- BOTTOM LINE -->
  <line x1="0" y1="height-1" x2="width" y2="height-1" color="#E2EEC8" />
</draw_ops>
<draw_ops name="round_overlay_active">
<!-- LEFT LINE -->
  <line x1="0" y1="5" x2="0" y2="height" color="#E2EEC8" />
<!-- TOP LINE -->
  <line x1="5" y1="0" x2="width" y2="0" color="#E2EEC8" />
<!-- RIGHT LINE -->
  <line x1="width-1" y1="0" x2="width-1" y2="height" color="#E2EEC8" />
<!-- BOTTOM LINE -->
  <line x1="0" y1="height-1" x2="width" y2="height-1" color="#E2EEC8" />

  <include name="tl_round_overlay_active" />
</draw_ops>

<draw_ops name="tl_round_overlay_inactive">
<!-- TOP LEFT ROUND -->
<!-- Default Corner Radius -->
  <line x1="3" x2="4" y1="1" y2="1" color="#D3CAAA" />
  <line x1="2" x2="2" y1="2" y2="2" color="#D3CAAA" />
  <line x1="1" x2="1" y1="3" y2="4" color="#D3CAAA" />

<!-- 20 Radius -->
<!-- V2
  <image filename="pix/tlcorner_inactive.png" x="1" y="1" width="21" height="21" alpha="1.0" />
-->
</draw_ops>
<draw_ops name="square_overlay_inactive">
<!-- LEFT LINE -->
  <line x1="0" y1="0" x2="0" y2="height" color="#D3CAAA" />
<!-- TOP LINE -->
  <line x1="1" y1="0" x2="width-1" y2="0" color="#D3CAAA" />
<!-- RIGHT LINE -->
  <line x1="width-1" y1="1" x2="width-1" y2="height" color="#D3CAAA" />
<!-- BOTTOM LINE -->
  <line x1="0" y1="height-1" x2="width" y2="height-1" color="#D3CAAA" />
</draw_ops>
<draw_ops name="round_overlay_inactive">
<!-- LEFT LINE -->
  <line x1="0" y1="5" x2="0" y2="height" color="#D3CAAA" />
<!-- TOP LINE -->
  <line x1="5" y1="0" x2="width" y2="0" color="#D3CAAA" />
<!-- RIGHT LINE -->
  <line x1="width-1" y1="0" x2="width-1" y2="height" color="#D3CAAA" />
<!-- BOTTOM LINE -->
  <line x1="0" y1="height-1" x2="width" y2="height-1" color="#D3CAAA" />

  <include name="tl_round_overlay_inactive" />
</draw_ops>


<!-- BUTTONS -->
<!-- INACTIVE BUTTON -->
<draw_ops name="inactive_button">
  <image filename="btn/inactive.png" x="0" y="0" width="16" height="16" />
</draw_ops>

<!-- CLOSE Button -->
<draw_ops name="close_active">
  <image filename="btn/active/close.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="close_inactive">
  <image filename="btn/inactive/close.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="close_prelight">
  <image filename="btn/prelight/close.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="close_pressed">
  <image filename="btn/pressed/close.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<!-- MENU/Un BUTTONS -->
<draw_ops name="un_menu_active">
  <image filename="btn/active/un_menu.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="un_menu_inactive">
  <image filename="btn/inactive/un_menu.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="un_menu_prelight">
  <image filename="btn/prelight/un_menu.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="un_menu_pressed">
  <image filename="btn/pressed/un_menu.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<!-- MINIMIZE BUTTON -->
<draw_ops name="min_active">
  <image filename="btn/active/min.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="min_inactive">
  <image filename="btn/inactive/min.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="min_prelight">
  <image filename="btn/prelight/min.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="min_pressed">
  <image filename="btn/pressed/min.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<!-- (un)MAXIMIZE BUTTON -->
<draw_ops name="mize_active">
  <image filename="btn/active/mize.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="mize_inactive">
  <image filename="btn/inactive/mize.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="mize_prelight">
  <image filename="btn/prelight/mize.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="mize_pressed">
  <image filename="btn/pressed/mize.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<!-- ABOVE/STICK BUTTONS -->
<draw_ops name="above_sticky_active">
<image filename="btn/active/above_sticky.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="above_sticky_inactive">
<image filename="btn/inactive/above_sticky.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="above_sticky_prelight">
<image filename="btn/prelight/above_sticky.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="above_sticky_pressed">
<image filename="btn/pressed/above_sticky.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<!-- SHADE button -->
<draw_ops name="shade_active">
  <image filename="btn/active/shade.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="shade_inactive">
  <image filename="btn/inactive/shade.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="shade_prelight">
  <image filename="btn/prelight/shade.png" x="0" y="0" width="16" height="16" />
</draw_ops>
<draw_ops name="shade_pressed">
  <image filename="btn/pressed/shade.png" x="0" y="0" width="16" height="16" />
</draw_ops>



<draw_ops name="outer_bevel">
<!--
  <rectangle color="gtk:fg[NORMAL]"
             x="0" y="0" width="width-1" height="height-1"/>
  <line color="gtk:light[NORMAL]"
        x1="1" y1="1" x2="1" y2="height-2"/>
  <line color="gtk:light[NORMAL]"
        x1="1" y1="1" x2="width-2" y2="1"/>
  <line color="gtk:dark[NORMAL]"
        x1="width-2" y1="1" x2="width-2" y2="height-2"/>
  <line color="gtk:dark[NORMAL]"
        x1="1" y1="height-2" x2="width-2" y2="height-2"/>
-->
</draw_ops>
<draw_ops name="focus_outline">
  <rectangle color="#E2EEC8"
             x="left_width-1" y="top_height-1"
             width="width-left_width-right_width+1"
             height="height-top_height-bottom_height+1"/>
</draw_ops>
<draw_ops name="focus_background">
  <include name="outer_bevel"/>
  <include name="focus_outline"/>
</draw_ops>
<draw_ops name="background_unfocused">
  <include name="outer_bevel"/>
  <include name="focus_outline"/>
</draw_ops>

<draw_ops name="title_text_focused_no_icon">
  <clip x="3" y="2" width="width-SpacerWidth-2" height="height-4"/>
  <!--<title color="#FFFFFF"  x="(3 `max` (width-title_width)) / 2+2" y="((height - title_height) / 2) `max` 0"/>-->
  <title color="#FFFFFF"  x="width-(icon_width+title_width)+16" y="((height - title_height) / 2) `max` 0"/>
</draw_ops>
<draw_ops name="title_text_no_icon">
  <clip x="3" y="2" width="width-SpacerWidth-2" height="height-4"/>
  <title color="#D3CAAA"  x="width-(icon_width+title_width)+16" y="((height - title_height) / 2) `max` 0"/>
</draw_ops>

<draw_ops name="title_normal">
  <include name="title_text_no_icon"/>
</draw_ops>
<draw_ops name="title_focused">
  <include name="title_text_focused_no_icon"/>
</draw_ops>

<draw_ops name="title_utility">
  <include name="title_text_no_icon"/>
</draw_ops>
<draw_ops name="title_utility_focused">
  <include name="title_text_focused_no_icon"/>
</draw_ops>

<draw_ops name="titlebar_active">
  <include name="mocha_bg" />
  <include name="title_hilight_active" />
</draw_ops>
<draw_ops name="titlebar_inactive">
  <include name="mocha_bg" />
  <include name="title_hilight_inactive" />
</draw_ops>
<draw_ops name="titlebar_blank">
  <include name="mocha_bg" />
</draw_ops>

<draw_ops name="leftside">
  <include name="mocha_bg" />
</draw_ops>
<draw_ops name="rightside">
  <include name="mocha_bg" />
</draw_ops>
<draw_ops name="bottomedge">
  <include name="mocha_bg" />
</draw_ops>


<frame_style name="normal_unfocused" geometry="normal"><!-- normal to rounded -->
  <piece position="entire_background" draw_ops="mocha_bg" />
  <piece position="title"             draw_ops="title_normal"/>
  <piece position="titlebar"          draw_ops="titlebar_inactive" />
  <piece position="left_edge"         draw_ops="leftside" />
  <piece position="right_edge"        draw_ops="rightside" />
  <piece position="bottom_edge"       draw_ops="bottomedge" />
  <piece position="overlay"           draw_ops="round_overlay_inactive" />


  <button function="close"    state="normal" draw_ops="close_inactive"/>
  <button function="minimize" state="normal" draw_ops="min_inactive"/>
  <button function="maximize" state="normal" draw_ops="mize_inactive"/>
  <button function="menu"     state="normal" draw_ops="un_menu_inactive"/>
<!-- Version 2 Window Buttons -->
<!-- V2
  <button function="shade"    state="normal" draw_ops="shade_inactive"/>
  <button function="above"    state="normal" draw_ops="above_sticky_inactive"/>
  <button function="stick"    state="normal" draw_ops="above_sticky_inactive"/>
  <button function="unshade"  state="normal" draw_ops="un_menu_inactive"/>
  <button function="unabove"  state="normal" draw_ops="un_menu_inactive"/>
  <button function="unstick"  state="normal" draw_ops="un_menu_inactive"/>
-->

  <button function="close"    state="prelight"  draw_ops="close_active"/>
  <button function="minimize" state="prelight"  draw_ops="min_active"/>
  <button function="maximize" state="prelight"  draw_ops="mize_active"/>
  <button function="menu"     state="prelight"  draw_ops="un_menu_active"/>
<!-- Version 2 Window Buttons -->
<!-- V2
  <button function="shade"    state="prelight"  draw_ops="shade_active"/>
  <button function="unshade"  state="prelight"  draw_ops="un_menu_active"/>
  <button function="above"    state="prelight"  draw_ops="above_sticky_active"/>
  <button function="unabove"  state="prelight"  draw_ops="un_menu_active"/>
  <button function="stick"    state="prelight"  draw_ops="above_sticky_active"/>
  <button function="unstick"  state="prelight"  draw_ops="un_menu_active"/>
-->

<!-- These are moot point because they will only work for _active_ windows. -->
  <button function="close"    state="pressed"   draw_ops="close_pressed"/>
  <button function="minimize" state="pressed"   draw_ops="min_pressed"/>
  <button function="maximize" state="pressed"   draw_ops="mize_pressed"/>
  <button function="menu"     state="pressed"   draw_ops="un_menu_pressed"/>
<!-- Version 2 Window Buttons -->
<!-- V2
  <button function="shade"    state="pressed"   draw_ops="shade_pressed"/>
  <button function="above"    state="pressed"   draw_ops="above_sticky_pressed"/>
  <button function="stick"    state="pressed"   draw_ops="above_sticky_pressed"/>
  <button function="unshade"  state="pressed"   draw_ops="un_menu_pressed"/>
  <button function="unabove"  state="pressed"   draw_ops="un_menu_pressed"/>
  <button function="unstick"  state="pressed"   draw_ops="un_menu_pressed"/>
-->
</frame_style>
<frame_style name="normal_focused" geometry="normal" parent="normal_unfocused">
  <piece position="entire_background" draw_ops="mocha_bg" />
  <piece position="title"     draw_ops="title_focused"/>
  <piece position="titlebar"  draw_ops="titlebar_active" />
  <piece position="overlay"   draw_ops="round_overlay_active" />

  <button function="close"    state="normal"    draw_ops="close_active"/>
  <button function="minimize" state="normal"    draw_ops="min_active"/>
  <button function="maximize" state="normal"    draw_ops="mize_active"/>
  <button function="menu"     state="normal"    draw_ops="un_menu_active"/>
  
  <button function="close"    state="prelight"  draw_ops="close_prelight"/>
  <button function="minimize" state="prelight"  draw_ops="min_prelight"/>
  <button function="maximize" state="prelight"  draw_ops="mize_prelight"/>
  <button function="menu"     state="prelight"  draw_ops="un_menu_prelight"/>

  
<!-- Version 2 Window Buttons -->
<!-- V2
  <button function="shade"    state="normal"    draw_ops="shade_active" />
  <button function="above"    state="normal"    draw_ops="above_sticky_active" />
  <button function="stick"    state="normal"    draw_ops="above_sticky_active" />
  <button function="unshade"  state="normal"    draw_ops="un_menu_active" />
  <button function="unabove"  state="normal"    draw_ops="un_menu_active" />
  <button function="unstick"  state="normal"    draw_ops="un_menu_active" />

  <button function="shade"    state="prelight"  draw_ops="shade_prelight" />
  <button function="above"    state="prelight"  draw_ops="above_sticky_prelight" />
  <button function="stick"    state="prelight"  draw_ops="above_sticky_prelight" />
  <button function="unshade"  state="prelight"  draw_ops="un_menu_prelight" />
  <button function="unabove"  state="prelight"  draw_ops="un_menu_prelight" />
  <button function="unstick"  state="prelight"  draw_ops="un_menu_prelight" />
-->

</frame_style>

<frame_style name="maximized_unfocused" parent="normal_unfocused" geometry="frame_maximized">
  <piece position="entire_background" draw_ops="blank"/>
  <piece position="overlay" draw_ops="blank" />
</frame_style>
<frame_style name="maximized_focused"   parent="normal_focused" geometry="frame_maximized">
  <piece position="entire_background" draw_ops="focus_outline"/>
  <piece position="overlay" draw_ops="blank" />
</frame_style>

<frame_style name="shade_focused"       parent="normal_focused"></frame_style>
<frame_style name="shade_unfocused"     parent="normal_unfocused"></frame_style>
<frame_style name="max_shade_focused"   parent="shade_focused"    geometry="frame_square" >
  <piece position="overlay" draw_ops="square_overlay_active" />
</frame_style>
<frame_style name="max_shade_unfocused" parent="shade_unfocused"  geometry="frame_square" >
  <piece position="overlay" draw_ops="square_overlay_inactive" />
</frame_style>

<frame_style name="utility_unfocused"   geometry="utility"  parent="normal_unfocused">
  <piece position="title" draw_ops="title_utility"/>
  <piece position="overlay" draw_ops="square_overlay_inactive" />
</frame_style>
<frame_style name="utility_focused"     geometry="utility"  parent="normal_focused">
  <piece position="title" draw_ops="title_utility_focused"/>
  <piece position="overlay" draw_ops="square_overlay_active" />
</frame_style>

<frame_style name="border_unfocused"    geometry="normal"   parent="normal_unfocused">
  <piece position="entire_background" draw_ops="outer_bevel"/>
  <piece position="title" draw_ops="blank"/>
  <piece position="overlay" draw_ops="square_overlay_inactive" />
  <piece position="titlebar" draw_ops="titlebar_blank" />
</frame_style>
<frame_style name="border_focused"      geometry="normal"   parent="normal_focused">
  <piece position="overlay" draw_ops="square_overlay_active" />
</frame_style>

<frame_style_set name="normal">
<frame focus="yes"  state="normal" resize="both"  style="normal_focused"/>
<frame focus="no"   state="normal" resize="both"  style="normal_unfocused"/>
<frame focus="yes"  state="maximized"             style="maximized_focused"/>
<frame focus="no"   state="maximized"             style="maximized_unfocused"/>
<frame focus="yes"  state="shaded"                style="shade_focused"/>
<frame focus="no"   state="shaded"                style="shade_unfocused"/>
<frame focus="yes"  state="maximized_and_shaded"  style="max_shade_focused"/>
<frame focus="no"   state="maximized_and_shaded"  style="max_shade_unfocused"/>
</frame_style_set>
<frame_style_set name="utility">
<frame focus="yes"  state="normal" resize="both"  style="utility_focused"/>
<frame focus="no"   state="normal" resize="both"  style="utility_unfocused"/>
<!-- this is a bunch of crack since utility windows shouldn't be maximized -->
<frame focus="yes"  state="maximized"             style="utility_focused"/>
<frame focus="no"   state="maximized"             style="utility_unfocused"/>
<frame focus="yes"  state="shaded"                style="shade_focused"/>
<frame focus="no"   state="shaded"                style="shade_unfocused"/>
<frame focus="yes"  state="maximized_and_shaded"  style="utility_focused"/>
<frame focus="no"   state="maximized_and_shaded"  style="utility_unfocused"/>
</frame_style_set>
<frame_style_set name="border">
<frame focus="yes"  state="normal" resize="both"  style="border_focused"/>
<frame focus="no"   state="normal" resize="both"  style="border_unfocused"/>
<frame focus="yes"  state="maximized"             style="border_focused"/>
<frame focus="no"   state="maximized"             style="border_unfocused"/>
<frame focus="yes"  state="shaded"                style="border_focused"/>
<frame focus="no"   state="shaded"                style="border_unfocused"/>
<frame focus="yes"  state="maximized_and_shaded"  style="border_focused"/>
<frame focus="no"   state="maximized_and_shaded"  style="border_unfocused"/>
</frame_style_set>

<window type="normal"       style_set="normal"/>
<window type="dialog"       style_set="normal"/>
<window type="modal_dialog" style_set="normal"/>
<window type="menu"         style_set="normal"/>
<window type="utility"      style_set="utility"/>
<window type="border"       style_set="border"/>

<!-- These are parsed but ignored. -->
<!--<menu_icon function="close"       state="normal" draw_ops="close_button_normal"/>
<menu_icon function="maximize"    state="normal" draw_ops="maximize_button_normal"/>
<menu_icon function="unmaximize"  state="normal" draw_ops="restore_button_normal"/>
<menu_icon function="minimize"    state="normal" draw_ops="minimize_button_normal"/>-->

</metacity_theme>

```

---

### Post by Copper Bezel on 2011-01-28
Sorry to bump this from time immemorial, but it was never solved and I now need this, as well. GnomeArt Tutorials isn't getting me anywhere. Personally I would have thought it should have been posted in Desktop Environments or Art and Design, so mods, feel free to move it if you deem it appropriate.

Edit: N/M, fixed it. Just the setting for "x" for the title text. I guess that should have been obvious, huh....

---

### Post by Habitual on 2011-01-29
[http://live.gnome.org/GnomeArt/Tutorials/GtkThemes](http://live.gnome.org/GnomeArt/Tutorials/GtkThemes)

---

