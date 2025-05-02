>?php
session_start();
if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    $username = $_POST['username'];

    // ডেমো ইউজারচেক (বাস্তবে ডাটাবেসে চেক করতে হবে)
    $allowed_users = ['user1', 'user2', 'admin'];

    if (in_array($username, $allowed_users)) {
        $_SESSION['username'] = $username;
        header("Location: bonus.php");
        exit();
    } else {
        $error = "ইউজারনেম ভুল!";
    }
}
?<!DOCTYPE html>
<html>
<head>
    <title>CK444 লগইন</title>
</head>
<body>
    <h2>CK444 লগইন</h2>
    <?php if (isset($error)) echo "<p style='color:red;'>$error</p>"; ?>
    <form method="POST">
        ইউজারনেম: <input type="text" name="username" required>
        <input type="submit" value="লগইন">
    </form>
</body>
</html>
