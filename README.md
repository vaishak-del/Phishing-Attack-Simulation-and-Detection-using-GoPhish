# Phishing-Attack-Simulation-and-Detection-using-GoPhish
A GoPhish-based phishing simulation in Kali Linux demonstrating a phishing email, fake login page, and tracking of user interaction, performed in a controlled lab for cybersecurity learning.
Overview

This lab demonstrates how a phishing attack works by simulating a controlled phishing campaign using GoPhish in a Kali Linux environment. The objective is to understand both the attacker’s methodology and the defender’s perspective in identifying phishing indicators and applying prevention techniques.

The simulation includes:

Configuring SMTP to send phishing emails

Designing a phishing email template

Creating a fake login landing page

Launching a phishing campaign

Tracking victim interaction

Analyzing phishing red flags and prevention strategies

This project is strictly performed in a lab using a test Gmail account.

Tool Used

GoPhish (open-source phishing framework)

Kali Linux

Gmail test account with App Password (SMTP)

Lab Setup
GoPhish Installation
wget https://github.com/gophish/gophish/releases/latest/download/gophish-v0.12.1-linux-64bit.zip
unzip gophish-v0.12.1-linux-64bit.zip -d gophish_lab
cd gophish_lab
chmod +x gophish
sudo ./gophish


Admin panel:

https://localhost:3333

SMTP Sending Profile Configuration

A test Gmail account was created for the lab.

Steps performed:

Enabled 2-Step Verification

Generated App Password

Unlocked Google CAPTCHA for SMTP access

GoPhish Sending Profile values:

Field	Value
Interface Type	SMTP
Host	smtp.gmail.com:587
Username	test Gmail address
Password	16-character App Password
Encryption	STARTTLS
From	IT Support testmail@gmail.com

A test email was successfully received, confirming SMTP functionality.

Email Template (Phishing Bait)

Subject:

Important: Your Email Password Expires Today


Body:

Hello {{.FirstName}},

Your email password is set to expire today.

Please reset your password immediately:

<a href="{{.URL}}">Reset Password</a>

IT Support Team

Landing Page (Fake Login Page)
<html>
<body>
<h2>Company Webmail Login</h2>
<form method="POST">
Username: <input name="username"><br><br>
Password: <input name="password" type="password"><br><br>
<input type="submit" value="Login">
</form>
</body>
</html>


Options enabled:

Capture submitted data

Redirect to google.com after submission

Target Group Creation

A user group was created with the test Gmail as the victim.

First Name	Last Name	Email	Position
Test	User	testmail@gmail.com
	Employee
Campaign Execution

Campaign configuration included:

Email template

Landing page

Sending profile

Target group

Kali machine IP as the phishing URL

The campaign was launched and the phishing email was received in the test Gmail inbox.

Results Observed in GoPhish Dashboard

The dashboard recorded:

Email opened

Link clicked

Credentials submitted

Timestamp and IP address

This confirms how attackers track victim interaction in real phishing attacks.

Phishing Red Flags Identified
Indicator	Reason
Urgent language	Creates panic and pressure
Unknown link	Not an official domain
Generic greeting	Not personalized
Credential request	Legitimate services do not ask via email
Prevention Techniques Learned

User awareness training

Checking URLs before clicking

Email filtering (SPF, DKIM, DMARC)

Multi-Factor Authentication

Reporting suspicious emails

Conclusion

This lab provided practical understanding of how phishing campaigns are created and executed, and how defenders can detect and prevent such attacks. The exercise strengthens knowledge in social engineering detection, email security, and blue team defensive strategies.

This simulation was performed strictly in a controlled lab environment using test accounts.
