# bgrm
Background resource manager

===== Overview =====

The idea of bgrm is to create a resource manager that operates by modifying the desktop background periodically
rather than other methods (such as conky) so that it will continue to show through transparent windows like terminals.

This setup makes heavy use of imagemagick's convert which can be used to composite images, then feh to set the background
as if it were a brand new background image.  There are probably other/better ways to do it, but it's really just a prototype
at the moment, so I may try to find ways to optimize the methods over time.  Currently this involves several steps (and is 
only prototyped with shell script), so there's definitely room for improvement.

After grabbing the values of each monitored resource, the script composites multiple images to form the final background.
Essentially this means there needs to be an individual .png with transparency for each potential status - which can be time
consuming to create.  However, customization of these images isn't too difficult provided you use image editing that supports
layers and batch processing to export them (in my case since I also develop on Windows I used Photoshop CS5).

The client-server process is similar, but adds an additional step.  You run the server version which awaits requests from your
client, and then passes the information back to the client to again composite the status images.  When using the shell script
this has an obvious performance impact (sometimes a 1-3 second delay) which is likely due to the methods I'm using combined with
using shellscripting for testing - but this may be able to be resolved as I move over to more efficient code, and may be less 
noticable on more powerful machines (I primarily run this on an i3 laptop).

