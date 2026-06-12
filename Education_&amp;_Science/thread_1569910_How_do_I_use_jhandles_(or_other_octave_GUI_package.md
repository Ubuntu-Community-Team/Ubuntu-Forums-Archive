---
title: "How do I use jhandles? (or other octave GUI packages)"
date: 2010-09-07
forum: Education &amp; Science
---

### Post by KIAaze on 2010-09-07
Hi,

I'm trying to make matlab GUIs run in octave.

I currently have octave installed on Windows with jhandles. I'm supposing the usage of jhandles is the same in Windows as under GNU/Linux.

Here's the test code I'm using (official MATLAB example):
simple_gui2.m
```
function simple_gui2
% SIMPLE_GUI2 Select a data set from the pop-up menu, then
% click one of the plot-type push buttons. Clicking the button
% plots the selected data in the axes.
 
   %  Create and then hide the GUI as it is being constructed.
   f = figure('Visible','off','Position',[360,500,450,285]);
 
   %  Construct the components.
   hsurf = uicontrol('Style','pushbutton','String','Surf',...
          'Position',[315,220,70,25],...
          'Callback',{@surfbutton_Callback});
   hmesh = uicontrol('Style','pushbutton','String','Mesh',...
          'Position',[315,180,70,25],...
          'Callback',{@meshbutton_Callback});
   hcontour = uicontrol('Style','pushbutton',...
          'String','Countour',...
          'Position',[315,135,70,25],...
          'Callback',{@contourbutton_Callback}); 
   htext = uicontrol('Style','text','String','Select Data',...
          'Position',[325,90,60,15]);
   hpopup = uicontrol('Style','popupmenu',...
          'String',{'Peaks','Membrane','Sinc'},...
          'Position',[300,50,100,25],...
          'Callback',{@popup_menu_Callback});
   ha = axes('Units','Pixels','Position',[50,60,200,185]); 
   align([hsurf,hmesh,hcontour,htext,hpopup],'Center','None');
   
   % Create the data to plot.
   peaks_data = peaks(35);
   membrane_data = membrane;
   [x,y] = meshgrid(-8:.5:8);
   r = sqrt(x.^2+y.^2) + eps;
   sinc_data = sin(r)./r;
   
   % Initialize the GUI.
   % Change units to normalized so components resize 
   % automatically.
   set([f,ha,hsurf,hmesh,hcontour,htext,hpopup],...
   'Units','normalized');
   %Create a plot in the axes.
   current_data = peaks_data;
   surf(current_data);
   % Assign the GUI a name to appear in the window title.
   set(f,'Name','Simple GUI')
   % Move the GUI to the center of the screen.
   movegui(f,'center')
   % Make the GUI visible.
   set(f,'Visible','on');
 
   %  Callbacks for simple_gui2. These callbacks automatically
   %  have access to component handles and initialized data 
   %  because they are nested at a lower level.
 
   %  Pop-up menu callback. Read the pop-up menu Value property
   %  to determine which item is currently displayed and make it
   %  the current data.
      function popup_menu_Callback(source,eventdata) 
         % Determine the selected data set.
         str = get(source, 'String');
         val = get(source,'Value');
         disp(str);
         disp(val);
         % Set current data to the selected data set.
         switch str{val};
         case 'Peaks' % User selects Peaks.
            current_data = peaks_data;
         case 'Membrane' % User selects Membrane.
            current_data = membrane_data;
         case 'Sinc' % User selects Sinc.
            current_data = sinc_data;
         end
      end
  
   % Push button callbacks. Each callback plots current_data in
   % the specified plot type.
 
   function surfbutton_Callback(source,eventdata) 
   % Display surf plot of the currently selected data.
      surf(current_data);
   end
 
   function meshbutton_Callback(source,eventdata) 
   % Display mesh plot of the currently selected data.
      mesh(current_data);
   end
 
   function contourbutton_Callback(source,eventdata) 
   % Display contour plot of the currently selected data.
      contour(current_data);
   end 
 
end

```

I get the following error when trying to run it:
```
octave-3.2.4.exe:9> simple_gui2
error: `uicontrol' undefined near line 10 column 9
error: called from:
error:   H:\MATLAB\simple_gui\simple_gui2.m at line 10, column 7
```

How do I use jhandles?
Is there currently any working solution for using uicontrol or equivalent in octave?

edit: Progress! :)
```
octave-3.2.4.exe:10> pkg load jhandles
warning: mark_as_command is obsolete and will be removed from a future version o
f Octave
octave-3.2.4.exe:11> simple_gui2
error: `align' undefined near line 27 column 4
error: called from:
error:   H:\MATLAB\simple_gui\simple_gui2.m at line 27, column 4
```
I guess jhandles is still a bit incomplete...

Modified code which runs, but does not work correctly (no figure displayed):
```
function simple_gui2
% SIMPLE_GUI2 Select a data set from the pop-up menu, then
% click one of the plot-type push buttons. Clicking the button
% plots the selected data in the axes.
 
   %  Create and then hide the GUI as it is being constructed.
   f = figure('Visible','off','Position',[360,500,450,285]);
 
   %  Construct the components.
   hsurf = uicontrol('Style','pushbutton','String','Surf',...
          'Position',[315,220,70,25],...
          'Callback',{@surfbutton_Callback});
   hmesh = uicontrol('Style','pushbutton','String','Mesh',...
          'Position',[315,180,70,25],...
          'Callback',{@meshbutton_Callback});
   hcontour = uicontrol('Style','pushbutton',...
          'String','Countour',...
          'Position',[315,135,70,25],...
          'Callback',{@contourbutton_Callback}); 
   htext = uicontrol('Style','text','String','Select Data',...
          'Position',[325,90,60,15]);
   hpopup = uicontrol('Style','popupmenu',...
          'String',{'Peaks','Membrane','Sinc'},...
          'Position',[300,50,100,25],...
          'Callback',{@popup_menu_Callback});
   ha = axes('Units','Pixels','Position',[50,60,200,185]); 
   % align([hsurf,hmesh,hcontour,htext,hpopup],'Center','None');
   
   % Create the data to plot.
   peaks_data = peaks(35);
   membrane_data = peaks();
   [x,y] = meshgrid(-8:.5:8);
   r = sqrt(x.^2+y.^2) + eps;
   sinc_data = sin(r)./r;
   
   % Initialize the GUI.
   %Create a plot in the axes.
   current_data = peaks_data;
   surf(current_data);
   % Assign the GUI a name to appear in the window title.
   set(f,'Name','Simple GUI')
   % Move the GUI to the center of the screen.
   % movegui(f,'center')
   % Make the GUI visible.
   set(f,'Visible','on');

   % Change units to normalized so components resize 
   % automatically.
   set([f,ha,hsurf,hmesh,hcontour,htext,hpopup],...
   'Units','normalized');
   
   %  Callbacks for simple_gui2. These callbacks automatically
   %  have access to component handles and initialized data 
   %  because they are nested at a lower level.
 
   %  Pop-up menu callback. Read the pop-up menu Value property
   %  to determine which item is currently displayed and make it
   %  the current data.
      function popup_menu_Callback(source,eventdata) 
         % Determine the selected data set.
         str = get(source, 'String');
         val = get(source,'Value');
         disp(str);
         disp(val);
         % Set current data to the selected data set.
         switch str{val};
         case 'Peaks' % User selects Peaks.
            current_data = peaks_data;
         case 'Membrane' % User selects Membrane.
            current_data = membrane_data;
         case 'Sinc' % User selects Sinc.
            current_data = sinc_data;
         end
      end
  
   % Push button callbacks. Each callback plots current_data in
   % the specified plot type.
 
   function surfbutton_Callback(source,eventdata) 
   % Display surf plot of the currently selected data.
      surf(current_data);
   end
 
   function meshbutton_Callback(source,eventdata) 
   % Display mesh plot of the currently selected data.
      mesh(current_data);
   end
 
   function contourbutton_Callback(source,eventdata) 
   % Display contour plot of the currently selected data.
      contour(current_data);
   end 
 
end

```

Still looking for a better solution... :'(

---

