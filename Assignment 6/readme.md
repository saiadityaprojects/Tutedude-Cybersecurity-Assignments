# Assignment 6 — Improper Session Management

**Name:** Sai Aditya  
**Platform:** TuteDude / TryHackMe  
**Category:** Cybersecurity — Web Application Security

## Objective

To investigate improper session management in a web application, examine session cookies, test whether client-side cookie manipulation affects user privileges, and identify the associated security vulnerability.

## Methodology

1. **Target access:** Connected to the assigned lab web application at the target IP address.
2. **Source code inspection:** Examined the page source and discovered the provided test credentials.
3. **Authentication:** Logged in to the SecureCorp employee portal using the lab credentials.
4. **Cookie inspection:** Used Firefox Developer Tools to inspect the browser's stored cookies.
5. **Cookie manipulation:** Modified the existing `user_role` cookie from `employee` to `admin` in the authorized lab environment.
6. **Verification:** Refreshed the dashboard and observed the flag displayed by the lab.
7. **Answer submission:** Submitted the discovered flag to the lab platform and verified that it was accepted.

## Key Findings

- The application stored a `user_role` value in a client-side cookie.
- Changing the role cookie to `admin` resulted in privilege escalation within the lab.
- The application displayed the flag:

  `FLAG{COOKIE_MANIPULATION_SUCCESS}`

- The lab demonstrated the risk of trusting client-controlled values for authorization decisions.

## Security Impact

If an application trusts a client-side cookie to determine a user's privileges without validating authorization on the server, a user may be able to obtain unauthorized access to privileged functionality.

## Recommended Mitigations

- Enforce authorization checks on the server for every protected request.
- Store authoritative roles and permissions on the server.
- Use secure session identifiers and validate sessions server-side.
- Apply appropriate cookie attributes, including `HttpOnly`, `Secure`, and `SameSite`, where applicable.
- Never rely on client-side cookie values alone to grant administrative privileges.

## Files

Upload the assignment report to this directory:

- `Assignment_6_Sai_Aditya.pdf` — Report containing the methodology, evidence screenshots, findings, and conclusion.

## Tools Used

- Firefox Developer Tools
- Web browser
- Assigned TuteDude / TryHackMe lab environment

## Learning Outcomes

- Understanding web application session management.
- Inspecting and analyzing browser cookies.
- Recognizing cookie-based privilege escalation.
- Understanding the importance of server-side authorization.
- Documenting security testing with supporting evidence.

## Disclaimer

All testing was performed in the assigned educational lab environment. Cookie manipulation and privilege-escalation testing should only be conducted on systems for which explicit authorization has been granted.
