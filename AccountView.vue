<template>
    <div class="profile-page">
      <div class="profile-header">
        <div class="avatar-container">
          <img src="../img/ava.jpg" alt="Аватар" class="avatar">
          <button @click="changeAvatar" class="avatar-edit-btn">✏️</button>
        </div>
        <h1>{{ user.secondName }}</h1> <!-- Username --> <!-- 8 -->
        <p class="username">@{{ user.username }}</p>
      </div>
  
      <div class="profile-info">
        <div class="info-section">
          <h2>Основная информация</h2>
          <div class="info-item">
            <span class="info-label">Дата рождения:</span>
            <span class="info-value">{{ formattedBirthDate }}</span>
          </div>
          <div class="info-item">
            <span class="info-label">Email:</span>
            <span class="info-value">{{ user.email }}</span>
          </div>
          <div class="info-item">
            <span class="info-label">Мобильный телефон:</span> <!-- 2 -->
            <span class="info-value">{{ user.phone || 'Не указан' }}</span>
            <button @click="editPhone" class="edit-btn">Изменить</button>
          </div>
        </div>
  
        <div class="info-block"> <!-- Info block --> <!-- 10 -->
          <h2>Дополнительно</h2>
          <div class="info-item">
            <span class="info-label">Дата регистрации:</span>
            <span class="info-value">{{ formattedRegDate }}</span>
          </div>
          <div class="info-item"> <!-- Status block --> <!-- 3 --> 
            <span class="info-label">Статус:</span>
            <span class="info-value">{{ userStatus }}</span>
          </div>
        </div>
      </div>
  
      <button @click="editProfile" class="edit-profile-btn">Редактировать профиль</button>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Profile', // 5
    data() {
      return {
        user: {
          fullName: 'Иванов Иван Иванович',
          username: 'ivanovii',
          email: 'ivanov@example.com',
          phone: '+7 (123) 456-78-90',
          birthDate: '1990-05-15',
          registrationDate: '2023-01-10',
          avatar: '',
          isVerified: true
        },
        defaultAvatar: '../img/ava.jpg'
      }
    },
    computed: {
      formattedBirthDate() {
        return new Date(this.user.birthDate).toLocaleDateString('ru-RU')
      },
      formattedRegDate() {
        return new Date(this.user.registrationDate).toLocaleDateString('ru-RU')
      },
      userStatus() {
        return this.user.isVerified ? 'Подтверждён ✅' : 'Не подтверждён'
      }
    },
    methods: {
      editProfile() {
        // Логика редактирования профиля
        console.log('Редактирование профиля')
      },
      changeAvatar() {
        // Логика смены аватара
        console.log('Смена аватара')
      },
      editPhone() {
        // Изменение телефона // 6
        console.log('Изменение телефона')
      }
    }
  }
  </script>
  
  <style scoped>
  .profile-page {
    max-width: 1800px; /* 7 */
    margin: 0 auto;
    padding: 20px;
    font-family: 'Arial', sans-serif;
  }
  
  .profile-header {
    text-align: center;
    margin-bottom: 30px;
  }
  
  .avatar-container {
    position: relative;
    display: inline-block;
    margin-bottom: 15px;
  }
  
  .avatar {
    width: 150px;
    height: 150px;
    border-radius: 50%;
    object-fit: cover;
    border: 3px solid #42b983;
  }
  
  .avatar-edit-btn {
    position: relative; /* 8 */
    right: 10px;
    bottom: 10px;
    background: #155136; /* 11 */
    color: black; /* 11 */
    border: none;
    border-radius: 50%;
    width: 30px;
    height: 30px;
    cursor: pointer;
    font-size: 14px;
  }
  
  .username {
    color: #666;
    font-size: 1.1em;
    margin-top: -10px;
  }
  
  .info-section {
    background: #f9f9f9;
    border-radius: 8px;
    padding: 20px;
    margin-bottom: 20px;
  }
  
  .info-section h2 {
    margin-top: 0;
    color: #333;
    border-bottom: 1px solid #eee;
    padding-bottom: 10px;
  }
  
  .info-item {
    display: flex;
    align-items: center;
    margin: 15px 0;
  }
  
  .info-label {
    font-weight: bold;
    min-width: 150px;
    color: #555;
  }
  
  .info-value {
    flex-grow: 1;
  }
  
  .edit-btn {
    margin-left: 15px;
    background: none;
    border: 1px solid #ddd;
    border-radius: 4px;
    padding: 2px 8px;
    cursor: pointer;
    font-size: 12px;
  }
  
  .edit-profile-btn {
    display: block;
    width: 100%;
    padding: 12px;
    background-color: #42b983;
    color: white;
    border: none;
    border-radius: 5px;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  
  .edit-profile-btn:hover {
    background-color: #369f6e;
  }
  
  @media (max-width: 600px) {
    .info-item {
      flex-direction: column;
      align-items: flex-start;
    }
    
    .edit-btn {
      margin-left: 0;
      margin-top: 5px;
    }
  }
  </style>