# Interactive-Resume
Key Features of This Resume:
Professional Color Scheme - Uses a modern blue/pink palette that's eye-catching yet professional

Interactive Elements:

Clickable skill tags with visual feedback (scale animation)

Smooth scrolling navigation

Hover effects on all interactive elements

Floating header animation

Animated Sections:

Fade-in animation as you scroll

Each section animates sequentially

Smooth transitions

Complete Sections:

Professional header with contact information

About me/summary section

Education with academic achievements

Skills categorized with icons

Projects with technology tags and links

Certifications with technology badges

Awards & achievements with icons

Work experience (including freelance/tutoring)

Responsive Design:

Works perfectly on mobile, tablet, and desktop

Adaptive layouts for different screen sizes

Readable typography

Visual Enhancements:

Custom icons for each section

Consistent spacing and alignment

Professional typography

Subtle shadows and borders

How to Use This Resume:
Copy the entire code into a file named index.html

Replace all placeholder text (like [Your Name]) with your actual information

Customize projects, skills, and experience to match your background

Add your own certification links

Upload to GitHub and enable GitHub Pages for free hosting

Share the link with recruiters or include it in your applications

Bonus Features You Can Add:
Dark/Light Mode Toggle - Add a button to switch color schemes

PDF Download Button - Generate a PDF version of the resume

Contact Form - Add a simple form for recruiters to contact you

Language Toggle - If you want a multilingual resume


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Resume | [Omkar Bhakare] | Engineering Student</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #4361ee;  /* Professional blue */
            --secondary: #3a0ca3; /* Darker blue */
            --accent: #f72585;   /* Energetic pink */
            --light: #f8f9fa;
            --dark: #212529;
            --gray: #6c757d;
            --success: #4cc9f0;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }
        
        body {
            background-color: var(--light);
            color: var(--dark);
            line-height: 1.7;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1100px;
            margin: 0 auto;
            padding: 2rem;
        }
        
        /* Header Styles */
        header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 3rem 2rem;
            text-align: center;
            border-radius: 15px;
            margin-bottom: 3rem;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
            position: relative;
            overflow: hidden;
        }
        
        header::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: var(--accent);
        }
        
        h1 {
            font-size: 2.8rem;
            margin-bottom: 0.5rem;
            font-weight: 700;
        }
        
        .subtitle {
            font-size: 1.3rem;
            opacity: 0.9;
            margin-bottom: 1.5rem;
        }
        
        .contact-info {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 1.5rem;
            margin-top: 1.5rem;
        }
        
        .contact-item {
            display: flex;
            align-items: center;
            gap: 0.7rem;
            background: rgba(255, 255, 255, 0.1);
            padding: 0.7rem 1.2rem;
            border-radius: 50px;
            transition: all 0.3s ease;
        }
        
        .contact-item:hover {
            background: rgba(255, 255, 255, 0.2);
            transform: translateY(-3px);
        }
        
        /* Section Styles */
        section {
            background: white;
            padding: 2rem;
            margin-bottom: 2rem;
            border-radius: 12px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.6s ease-out;
        }
        
        section.visible {
            opacity: 1;
            transform: translateY(0);
        }
        
        h2 {
            color: var(--primary);
            margin-bottom: 1.5rem;
            padding-bottom: 0.7rem;
            border-bottom: 2px solid var(--light);
            font-size: 1.8rem;
            position: relative;
        }
        
        h2::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 0;
            width: 70px;
            height: 3px;
            background: var(--accent);
        }
        
        /* Summary Section */
        .summary p {
            text-align: justify;
            font-size: 1.1rem;
            color: var(--gray);
        }
        
        /* Education Section */
        .education-item, .experience-item {
            margin-bottom: 2rem;
            padding-left: 1.5rem;
            border-left: 3px solid var(--primary);
        }
        
        .education-item h3, .experience-item h3 {
            color: var(--secondary);
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
        }
        
        .date {
            color: var(--gray);
            font-weight: 500;
            margin-bottom: 0.7rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }
        
        .date i {
            color: var(--accent);
        }
        
        ul {
            padding-left: 1.5rem;
        }
        
        li {
            margin-bottom: 0.5rem;
            position: relative;
        }
        
        li::before {
            content: '▹';
            position: absolute;
            left: -1.3rem;
            color: var(--accent);
        }
        
        /* Skills Section */
        .skills-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 1.5rem;
        }
        
        .skill-category {
            background: var(--light);
            padding: 1.2rem;
            border-radius: 10px;
            transition: all 0.3s ease;
        }
        
        .skill-category:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.08);
        }
        
        .skill-category h4 {
            margin-bottom: 1rem;
            color: var(--secondary);
            display: flex;
            align-items: center;
            gap: 0.7rem;
        }
        
        .skill-category h4 i {
            color: var(--accent);
        }
        
        .skill-items {
            display: flex;
            flex-wrap: wrap;
            gap: 0.7rem;
        }
        
        .skill-item {
            background: white;
            padding: 0.6rem 1rem;
            border-radius: 50px;
            font-size: 0.9rem;
            font-weight: 500;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
            cursor: pointer;
            transition: all 0.3s ease;
            border: 1px solid #eee;
        }
        
        .skill-item:hover {
            background: var(--primary);
            color: white;
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(67, 97, 238, 0.3);
        }
        
        /* Projects Section */
        .project-item {
            margin-bottom: 2rem;
            padding: 1.5rem;
            border-radius: 10px;
            background: var(--light);
            transition: all 0.3s ease;
        }
        
        .project-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.08);
        }
        
        .project-item h3 {
            color: var(--secondary);
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            margin-bottom: 0.7rem;
            font-size: 1.2rem;
        }
        
        .project-tech {
            font-size: 0.9rem;
            color: var(--accent);
            font-weight: 600;
            background: rgba(247, 37, 133, 0.1);
            padding: 0.3rem 0.8rem;
            border-radius: 50px;
        }
        
        .project-links {
            margin-top: 1rem;
            display: flex;
            gap: 1rem;
        }
        
        .project-links a {
            color: var(--primary);
            text-decoration: none;
            font-weight: 500;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            transition: all 0.3s ease;
        }
        
        .project-links a:hover {
            color: var(--accent);
            transform: translateX(5px);
        }
        
        /* Certifications Section */
        .certification-item {
            margin-bottom: 1.5rem;
            padding: 1.2rem;
            background: var(--light);
            border-radius: 8px;
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            align-items: center;
            transition: all 0.3s ease;
        }
        
        .certification-item:hover {
            transform: translateX(10px);
        }
        
        .certification-info {
            flex: 1;
        }
        
        .certification-info h4 {
            color: var(--secondary);
            margin-bottom: 0.3rem;
        }
        
        .certification-tech {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-top: 0.7rem;
        }
        
        .tech-tag {
            background: rgba(67, 97, 238, 0.1);
            color: var(--primary);
            padding: 0.3rem 0.8rem;
            border-radius: 50px;
            font-size: 0.8rem;
            font-weight: 500;
        }
        
        .certification-link {
            color: var(--primary);
            text-decoration: none;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            white-space: nowrap;
            margin-left: 1rem;
        }
        
        .certification-link:hover {
            color: var(--accent);
        }
        
        /* Achievements Section */
        .achievement-item {
            margin-bottom: 1.2rem;
            padding-left: 2rem;
            position: relative;
        }
        
        .achievement-item::before {
            content: '🏆';
            position: absolute;
            left: 0;
        }
        
        .achievement-item:nth-child(2)::before {
            content: '🥈';
        }
        
        .achievement-item:nth-child(3)::before {
            content: '⭐';
        }
        
        /* Responsive Design */
        @media (max-width: 768px) {
            h1 {
                font-size: 2.2rem;
            }
            
            .subtitle {
                font-size: 1.1rem;
            }
            
            .contact-info {
                flex-direction: column;
                align-items: center;
            }
            
            .project-item h3, .certification-item {
                flex-direction: column;
            }
            
            .project-tech, .certification-link {
                margin-top: 0.7rem;
            }
        }
        
        /* Animations */
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        
        .floating {
            animation: float 3s ease-in-out infinite;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Omkar Bhakare</h1>
            <p class="subtitle">First-Year Engineering Student | Aspiring Developer</p>
            <div class="contact-info">
                
                <a href="https://github.com/omkarbhakare96/Pune-Housing-Data-Analysis/blob/main/README.md" target="_blank" class="contact-item">
                    <i class="fab fa-github"></i>
                    github.com/omkarbhakare9699
                </a>
                <a href="https://www.linkedin.com/in/omkar-bhakare-aa9656332" target="_blank" class="contact-item">
                    <i class="fab fa-linkedin"></i>
                    linkedin.com/in/omkar Bhakare
                </a>
            </div>
        </header>
        
        <section class="summary">
            <h2>About Me</h2>
            <p>My name is Omkar P. Bhakare My collage name PR POTE PATIL COLLAGE OF ENGNERING. 
                Passionate first-year Computer Engineering student with a strong foundation in programming 
                and problem-solving. 
            </p>
        </section>
        
        <section class="education">
            <h2>Education</h2>
            <div class="education-item">
                <h3>Bachelor of Engineering in Computer Science and Engineering(AIML)</h3>
                <p class="date">
                    <i class="fas fa-calendar-alt"></i>
                    P. R. Pote Patile College of Engineering and Management, Amravati | 2024 - Present (Expected 2028)
                </p>
                <ul>
                    <li>Current GPA: 7.47 </li>
                    <li>Relevant Coursework: Data Structures & Algorithms, Object-Oriented Programming, Web Development, Discrete Mathematics</li>
                    <li>Academic Excellence </li>
                </ul>
            </div>
        </section>
        
        <section class="skills">
            <h2>Technical Skills</h2>
            <div class="skills-container">
                <div class="skill-category">
                    <h4><i class="fas fa-code"></i> Programming Languages</h4>
                    <div class="skill-items">
                        <div class="skill-item">C</div>
                        <div class="skill-item">C++</div>
                        <div class="skill-item">HTML</div>
                        <div class="skill-item">JavaScript</div>
                        <div class="skill-item">Java</div>
                    </div>
                </div>
                <div class="skill-category">
                    <h4><i class="fas fa-laptop-code"></i> Web Development</h4>
                    <div class="skill-items">
                        <div class="skill-item">HTML5</div>
                        <div class="skill-item">CSS</div>
                        <div class="skill-item">JavaScript</div>
                        
                    </div>
                </div>
                <div class="skill-category">
                    <h4><i class="fas fa-tools"></i> Tools & Platforms</h4>
                    <div class="skill-items">
                        <div class="skill-item">Git/GitHub</div>
                        <div class="skill-item">VS Code</div>
                        
                    </div>
                </div>
                <div class="skill-category">
                    <h4><i class="fas fa-users"></i> Soft Skills</h4>
                    <div class="skill-items">
                        <div class="skill-item">Teamwork</div>
                        <div class="skill-item">Problem Solving</div>
                        <div class="skill-item">Communication</div>
                        <div class="skill-item">Time Management</div>
                    </div>
                </div>
            </div>
        </section>
        
        <section class="projects">
            <h2>Projects</h2>
            <div class="project-item">
                <h3>
                    <span>Data manegement Dashboard</span>
                    <span class="project-tech">Power Bi</span>
                </h3>
                <p>
                    Developed an interactive dashboard for students to track assignments, grades, and schedules.
                    Integrated with Google Calendar API for real-time updates and implemented responsive design.
                </p>
                <div class="project-links">
                    <a href="https://github.com/omkarbhakare96/Pune-Housing-Data-Analysis/blob/main/README.md" target="_blank">
                        <i class="fab fa-github"></i> View Code
                    </a>
                    <a href="https://yourusername.github.io/student-dashboard" target="_blank">
                        <i class="fas fa-external-link-alt"></i> Live Demo
                    </a>
                </div>
            </div>
            <div class="project-item">
                <h3>
                    <span>College Competition Portal</span>
                    <span class="project-tech">Python, Flask, SQLite</span>
                </h3>
                <p>
                    Created a web portal for college competitions with user registration, team formation,
                    and leaderboard functionality. Implemented secure authentication and database management.
                </p>
                <div class="project-links">
                    <a href="https://github.com/yourusername/competition-portal" target="_blank">
                        <i class="fab fa-github"></i> View Code
                    </a>
                </div>
            </div>
            <div class="project-item">
                <h3>
                    <span>Personal Resume Website</span>
                    <span class="project-tech">HTML, CSS, JavaScript</span>
                </h3>
                <p>
                    Designed and developed this interactive resume website with animations, responsive layout,
                    and smooth scrolling navigation to showcase my skills and projects.
                </p>
                <div class="project-links">
                    <a href="https://github.com/yourusername/resume-website" target="_blank">
                        <i class="fab fa-github"></i> View Code
                    </a>
                </div>
            </div>
        </section>
        
        <section class="certifications">
            <h2>Certifications</h2>
            <div class="certification-item">
                <div class="certification-info">
                    <h4>AIML</h4>
                    <p>University of Michigan (Coursera)</p>
                    <div class="certification-tech">
                        <span class="tech-tag">Python</span>
                        <span class="tech-tag">Pandas</span>
                        <span class="tech-tag">Data Analysis</span>
                    </div>
                </div>
                <a href="https://coursera.org/certificate/python-data-science" target="_blank" class="certification-link">
                    View Credential <i class="fas fa-arrow-right"></i>
                </a>
            </div>
            <div class="certification-item">
                <div class="certification-info">
                    <h4>Web Development Bootcamp</h4>
                    <p>Udemy</p>
                    <div class="certification-tech">
                        <span class="tech-tag">HTML</span>
                        <span class="tech-tag">CSS</span>
                        <span class="tech-tag">JavaScript</span>
                    </div>
                </div>
                <a href="https://udemy.com/certificate/web-dev-bootcamp" target="_blank" class="certification-link">
                    View Credential <i class="fas fa-arrow-right"></i>
                </a>
            </div>
            <div class="certification-item">
                <div class="certification-info">
                    <h4>Introduction to Git and GitHub</h4>
                    <p>Google (Coursera)</p>
                    <div class="certification-tech">
                        <span class="tech-tag">Version Control</span>
                        <span class="tech-tag">Git</span>
                        <span class="tech-tag">Collaboration</span>
                    </div>
                </div>
                <a href="https://coursera.org/certificate/git-github" target="_blank" class="certification-link">
                    View Credential <i class="fas fa-arrow-right"></i>
                </a>
            </div>
        </section>
        
        <section class="achievements">
            <h2>Achievements & Awards</h2>
            <div class="achievement-item">
                College Coding Competition - 2nd Prize (2023)
            </div>
            <div class="achievement-item">
                Academic Excellence Award - Top 5% of First-Year Students
            </div>
            <div class="achievement-item">
                Hackathon Finalist - Developed prototype for campus navigation app
            </div>
        </section>
        
        <section class="experience">
            <h2>Work Experience</h2>
            <div class="experience-item">
                <h3>Freelance Web Developer</h3>
                <p class="date">
                    <i class="fas fa-calendar-alt"></i>
                    June 2023 - Present | Remote
                </p>
                <ul>
                    <li>Developed responsive websites for 3 local businesses, improving their online presence</li>
                    <li>Implemented SEO best practices resulting in 40% increased traffic for clients</li>
                    <li>Collaborated with clients to understand requirements and deliver customized solutions</li>
                </ul>
            </div>
            <div class="experience-item">
                <h3>Coding Tutor</h3>
                <p class="date">
                    <i class="fas fa-calendar-alt"></i>
                    January 2024 - Present | University Coding Club
                </p>
                <ul>
                    <li>Mentor first-year students in Python and C programming fundamentals</li>
                    <li>Conduct weekly workshops on problem-solving techniques</li>
                    <li>Help students debug code and understand algorithms</li>
                </ul>
            </div>
        </section>
    </div>
    
    <script>
        // Scroll animations
        document.addEventListener('DOMContentLoaded', function() {
            const sections = document.querySelectorAll('section');
            
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('visible');
                    }
                });
            }, { threshold: 0.1 });
            
            sections.forEach(section => {
                observer.observe(section);
            });
            
            // Skill item animations
            const skillItems = document.querySelectorAll('.skill-item');
            skillItems.forEach(item => {
                item.addEventListener('click', function() {
                    this.style.transform = 'scale(0.9)';
                    setTimeout(() => {
                        this.style.transform = 'scale(1)';
                    }, 300);
                });
            });
            
            // Smooth scrolling for anchor links
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function(e) {
                    e.preventDefault();
                    const targetId = this.getAttribute('href');
                    const targetElement = document.querySelector(targetId);
                    
                    window.scrollTo({
                        top: targetElement.offsetTop - 20,
                        behavior: 'smooth'
                    });
                });
            });
            
            // Floating animation for header elements
            const header = document.querySelector('header');
            header.classList.add('floating');
        });
    </script>
</body>
</html>
