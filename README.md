# Smart_Security_Camera
IoT Raspberry Pi security camera running OpenCV for object detection. The camera will send an email with an image of any objects it detects.

step 1: This project uses openCV to detect objects in the video feed. You can install openCV by using the following tutorial.

https://github.com/recroviral/picam

Step 2: Clone the repo:

$ git clone https://github.com/HackerShackOfficial/Smart-Security-Camera

Step 3: Next, Nevigate to the repository directory

$ cd Smart-Security-Camera

and install the dependancy for the project

for python2.7

$ pip install -r requirement.txt

for python3

$ pip3 install -r requirement.txt

Step 4: To get emails when objects are detected, you'll need to make a couple modifications to the mail.py file.

Open mail.py with vim 

$ vim mail.py 

then press i to edit. Scroll down to the following section

# Email you want to send the update from (only works with gmail)
fromEmail = 'myemail@gmail.com'
fromEmailPassword = 'password1234'
# Email you want to send the update to
toEmail = 'anotheremail@gmail.com'

and replace with your own email/credentials. The mail.py file logs into a gmail SMTP server and sends an email with an image of the object detected by the security camera.

Press esc then ZZ to save and exit.

You can also modify the main.py file to change some other properties.

email_update_interval = 600 # sends an email only once in this time interval
video_camera = VideoCamera(flip=True) # creates a camera object, flip vertically
object_classifier = cv2.CascadeClassifier("models/fullbody_recognition_model.xml") # an opencv classifier

Notably, you can use a different object detector by changing the path "models/fullbody_recognition_model.xml" in object_classifier =cv2.CascadeClassifier("models/fullbody_recognition_model.xml")

to a new model in the models directory.

facial_recognition_model.xml
fullbody_recognition_model.xml
upperbody_recognition_model.xml

for python3 you have to make some changes in import library in mail.py

from email.mime.multipart import MIMEMultipart    #from email.MIMEMultipart import MIMEMultipart

from email.mime.text import MIMEText              #from email.MIMEtext import MIMEText

from email.mime.image import MIMEImage            ##from email.MIMEImage import MIMEImage

and in main.py make the bracket to each print statement

For Example,

print "Sending email..."     change to     print ("Sending Email")

or you can replase the mail.py and main.py given into this repository

Run the Program

for python2.7

$ python main.py

for python3

$ python3 main.py


Receiving Emails
When receiving an email for the first time, you might get the notification from Google.

By default, Google blocks apps from using SMTP without permissions. We can solve this by clicking on the allow "less secure apps" link and toggle the feature on. The next object detected will send an email.
